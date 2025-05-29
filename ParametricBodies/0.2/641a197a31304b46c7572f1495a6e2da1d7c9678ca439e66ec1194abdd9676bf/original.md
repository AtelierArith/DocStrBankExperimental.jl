```
interpNurbs(pnts{D,n};p=n-1)
```

Given a `SMatrix{D ∈ [2,3],n}` of points, fits a `NurbsCurve{D,n}` of degree `p` to  this set of points. By default the highest degrees NURBS is constructed.
