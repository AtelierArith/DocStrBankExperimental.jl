```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, cone::MOI.PositiveSemidefiniteConeTriangle) where {T}
```

derivative of projection of vector `v` on positive semidefinite cone i.e. K = S^n⨥

References:

  * [Proximal Algorithms](https://doi.org/10.1561/2400000003), Section 6.3.3, p. 189
