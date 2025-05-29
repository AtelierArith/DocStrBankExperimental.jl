```
readpng(pathname)
```

Read a PNG file.

This returns a image object suitable for placing on the current drawing with `placeimage()`. You can access its `width` and `height` fields:

```
image = readpng("test-image.png")
w = image.width
h = image.height
```
