```
inout = inbbox(x::Real, y::Real, bbox) -> Bool
```

Find out if points `x,y` are inside a bounding box.

  * `x, y`: point coordinates.
  * `bbox` is a 4-element array (vector, matrix or tuple) with xmin, xmax, ymin, ymax.

### Returns

`true` for points inside the bounding box and `false` for those outside
