```
placeimage(img, pt::Point=O, alpha; centered=false)
placeimage(pngimg, xpos, ypos, alpha; centered=false)
```

Place a PNG image `pngimg` on the drawing at `pt` or `Point(xpos, ypos)` with opacity/transparency `alpha`. The image has been previously loaded using `readpng()`.

Use keyword `centered=true` to place the center of the image at the position.
