# Miro mindmap export

This is a short development script to export miro (https://miro.com/index/) mindmaps in a structured form.

## Why?

Miro provides various export options for boards, including image, pdf and csv. However, at the time of writing, if you export a mindmap as csv you just get the flat text: you lose all the relational information (i.e. how the concepts are linked together). Which is annoying if you want to use the data in a different application.

It looks like structured export might be on the roadmap:

 - see FAQ 6 https://help.miro.com/hc/en-us/articles/360017730753-Mind-Map
 - and this community question https://community.miro.com/developer-platform-forum-57/how-to-export-mindmap-as-a-json-616
 
But in the meantime here's a script to get started.

## JSON export

The idea is to export the mindmap as a nested json object in the form:

```
{miro_id: {text:"string", branches:{}}}
```

The top level is the central starting concept. Its branches are the concepts that it is linked to, and so on.
See the example mind_map.json

## Limitations

The code is set out in export_mindmap.ipynb. I've done this in a notebook because it is just a sketch and expect folk will want to work with it interactively.

A few notes:

 - You'll need to get setup with a miro dev team and API token. See https://developers.miro.com/docs/getting-started
 - The script assumes: (i) the board's only content is a single mindmap (i.e. you don't have other notes / widgets and there is only one mindmap); and (ii) the mindmap is an (n-ary) tree (i.e. there are no links between different branches). However, it should not be hard to adapt it around these assumptions.
 - Implementation notes are included in the notebook. There will undoubtedly be better / more pythonic ways of achieving this result and comments are welcome.
