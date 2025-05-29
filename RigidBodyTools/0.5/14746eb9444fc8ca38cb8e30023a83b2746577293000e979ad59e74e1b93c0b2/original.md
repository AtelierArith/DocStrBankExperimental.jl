```
Ellipse(a,b,n[,endpointson=false],[shifted=false]) <: Body
```

Construct an elliptical body with semi-major axis `a` and semi-minor axis `b`, with `n` points distributed on the body perimeter. Can also call this with `Ellipse(a,b,ds)` where `ds` is the desired spacing between points. If `endpointson=true`, then the endpoints will be placed on the surface and the midpoints will lie inside the nominal ellipse. By default, the midpoints lie on the ellipse. If `shifted=true`, then the first endpoint lies on an axis of symmetry. By default the first midpoint lies on the axis symmetry.
