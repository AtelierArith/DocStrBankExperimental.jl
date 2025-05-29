```
(l::NurbsLocator)(x,t)
```

Estimate the parameter value `u⁺ = argmin_u (x-curve(u,t))²` for a NURBS by looping through the  spline segments.
