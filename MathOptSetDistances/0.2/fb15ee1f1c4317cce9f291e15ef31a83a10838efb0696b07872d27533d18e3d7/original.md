```
projection_on_set(::NormedEpigraphDistance{p}, v::AbstractVector{T}, ::MOI.SecondOrderCone) where {T}
```

projection of vector `v` on second order cone i.e. K = {(t, x) ∈ R+ × Rn |  ||x|| ≤ t }
