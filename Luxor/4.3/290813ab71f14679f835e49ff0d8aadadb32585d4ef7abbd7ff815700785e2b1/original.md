```
placeimage(buffer::AbstractMatrix{ARGB32}, args...;
    kargs...)
```

Place an array of ARGB32 lements on the drawing at `pos` with opacity/transparency `alpha`. Values are "alpha-premultiplied" before being placed.

Use keyword `centered=true` to place the center of the image at the position.
