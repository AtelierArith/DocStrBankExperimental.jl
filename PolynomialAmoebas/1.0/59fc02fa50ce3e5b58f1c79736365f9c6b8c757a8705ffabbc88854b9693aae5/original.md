```
newtonpolygon(p::AbstractPolynomial; lowerhull=false)
```

Construct a [`NewtonPolygon`](@ref) from the support of the polynomial `p`. `lowerhull` indicates whether the lower or upper convex hull should be used to construct the regular subdivision of the Newton polygon.
