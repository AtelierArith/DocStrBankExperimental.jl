```
updatebox!(box::AbstractVector, x::AbstractArray)
```

Update a box with another location, or create a new box.

If the  `box` does not have  the correct dimensions,  it is correctly sized.

`box` = bounding box     for 1-D `box=[minx,maxx]`, or     for 2-D `box=[minx,maxx,miny,maxy]`, or     for 3-D `box=[minx,maxx,miny,maxy,minz,maxz]`     The `box` is expanded to include the     supplied location `x`.   The variable `x`  can hold multiple points in rows.
