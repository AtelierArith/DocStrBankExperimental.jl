```
projection_gradient_on_set(::NormedEpigraphDistance{p}, v::AbstractVector{T}, ::MOI.SecondOrderCone) where {T}
```

ベクトル `v` の第二次円錐への射影の導関数、すなわち K = {(t, x) ∈ R+ × Rn |  ||x|| ≤ t }

参考文献:

  * [Proximal Algorithms](https://doi.org/10.1561/2400000003), Section 6.3.2, p. 189
