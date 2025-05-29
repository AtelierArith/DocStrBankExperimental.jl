pointinconvexpoly - Determine if a 2D point is within a convex polygon

```
Usage:  v = pointinconvexpoly(p, poly)

Arguments:   p - 2-vector specifying the point.
          poly - Convex polygon defined as a series of vertices in
                 sequence, clockwise or anticlockwise around the polygon as
                 a 2 x N array.

Returns:    v - +1 if within the polygon
                -1 if outside
                 0 if on the boundary
```

Note:  There is no check to see if the polygon is indeed convex, use isconvexpoly() if needed

See also: isconvexpoly()
