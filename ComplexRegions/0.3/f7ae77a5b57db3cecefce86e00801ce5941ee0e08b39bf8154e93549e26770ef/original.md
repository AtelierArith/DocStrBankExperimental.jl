```
truncate(P::Union{CircularPolygon,Polygon},C::Circle)
```

Compute a trucated form of the polygon by replacing each pair of rays incident at infinity with two segments connected by an arc along the given circle. This is *not* a true clipping of the polygon, as finite sides are not altered. The result is either a CircularPolygon or the original `P`.
