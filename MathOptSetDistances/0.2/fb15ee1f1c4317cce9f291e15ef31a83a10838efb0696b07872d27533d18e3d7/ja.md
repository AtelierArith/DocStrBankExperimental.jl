```
projection_on_set(::NormedEpigraphDistance{p}, v::AbstractVector{T}, ::MOI.SecondOrderCone) where {T}
```

ベクトル `v` の第二次円錐への射影、すなわち K = {(t, x) ∈ R+ × Rn |  ||x|| ≤ t }
