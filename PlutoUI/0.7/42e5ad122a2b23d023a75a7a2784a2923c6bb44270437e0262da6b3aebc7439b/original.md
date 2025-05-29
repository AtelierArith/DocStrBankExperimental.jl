Create a `Resource` for a local file (a base64 encoded data URL is generated).

# WARNING

`LocalResource` **will not work** when you share the script/notebook with someone else, *unless they have those resources at exactly the same location on their file system*. 

## Recommended alternatives (images)

1. Go to [imgur.com](https://imgur.com) and drag&drop the image to the page. Right click on the image, and select "Copy image location". You can now use the image like so: `PlutoUI.Resource("https://i.imgur.com/SAzsMMA.jpg")`.
2. If your notebook is part of a git repository, place the image in the repository and use a relative path: `PlutoUI.LocalResource("../images/cat.jpg")`.

# Examples

```
LocalResource("./cat.jpg")
```

```
LocalResource("/home/fons/Videos/nijmegen.mp4", :width => 200)
```

```
md"""
This is what a duck sounds like: $(LocalResource("../data/hannes.mp3"))
md"""
```
