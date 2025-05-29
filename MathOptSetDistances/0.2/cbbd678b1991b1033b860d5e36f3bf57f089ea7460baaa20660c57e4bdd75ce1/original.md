```
projection_gradient_on_set(::NormedEpigraphDistance{p}, v::AbstractVector{T}, ::MOI.SecondOrderCone) where {T}
```

derivative of projection of vector `v` on second order cone i.e. K = {(t, x) ∈ R+ × Rn |  ||x|| ≤ t }

References:

  * [Proximal Algorithms](https://doi.org/10.1561/2400000003), Section 6.3.2, p. 189
