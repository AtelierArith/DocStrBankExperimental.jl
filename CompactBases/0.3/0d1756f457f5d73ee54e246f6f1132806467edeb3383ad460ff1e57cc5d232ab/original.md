```
basis_transform(A::BSplineOrRestricted, B::AbstractFiniteDifferences)
```

This works via Vandermonde interpolation, which is potentially unstable. In this case, we do not provide [`basis_overlap`](@ref).
