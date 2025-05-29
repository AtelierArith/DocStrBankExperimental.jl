```
max_pixrad(res::Resolution, ring)
max_pixrad(res::Resolution)
```

Return the maximum angular distance (in radians) between a pixel center and any of its corners. If `ring` is specified, the result applies to all the pixels of the given ring; otherwise, all the pixels on the sphere are considered.
