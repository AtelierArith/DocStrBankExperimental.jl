convexpolyintersect - Returns true if convex polygons intersect.

```
Usage:  intersect = convexpolyintersect(p1, p2) 

Arguments:  p1, p2 - The two convex polygons to be tested where the
                     polygons are defined as 2xN arrays of vertex
                     coordinates in sequence around the polygon.

Returns:             Boolean result.
```

Note: There is no check to see if the polygons are indeed convex, use isconvexpoly() if needed

See also: isconvexpoly(), rectintersect()
