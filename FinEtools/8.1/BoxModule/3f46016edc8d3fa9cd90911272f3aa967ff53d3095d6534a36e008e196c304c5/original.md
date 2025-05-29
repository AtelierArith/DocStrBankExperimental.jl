```
inbox(box::AbstractVector, x::AbstractVector)
```

Is the given location inside the box?

  * `box` = vector entries arranged as [minx,maxx,miny,maxy,minz,maxz](or adjusted for lower space dimension).

Note: point on the boundary of the box is counted as being inside.
