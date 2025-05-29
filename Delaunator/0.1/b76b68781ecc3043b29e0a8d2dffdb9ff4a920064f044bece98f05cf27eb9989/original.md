```
segments(p::InfinitePolygon; [dist = eps()])
```

Return an iterator over linesegments involved in the polygon. If the polygon is infinite, then this will not be closed and the first two points will be along the incoming ray and the last two points will be along the outgoing ray (each will be an arbitrary  length along this ray)

If the polygon is finite, then it will be closed.
