```
boundingbox(x::AbstractArray)
```

Compute the bounding box of the points in `x`.

`x` = holds points, one per row.

Returns `box` = bounding box     for 1-D `box=[minx,maxx]`, or     for 2-D `box=[minx,maxx,miny,maxy]`, or     for 3-D `box=[minx,maxx,miny,maxy,minz,maxz]`
