```
rect(xmin, ymin, w, h; action=:none)
rect(xmin, ymin, w, h, action)
```

Create a rectangle with one corner at (`xmin`/`ymin`) with width `w` and height `h`, and add it to the current path. Then apply `action`.

Returns a tuple of two points, the corners of a bounding box that encloses the rectangle.

See `box()` for more ways to do similar things, such as supplying two opposite corners, placing by centerpoint and dimensions.
