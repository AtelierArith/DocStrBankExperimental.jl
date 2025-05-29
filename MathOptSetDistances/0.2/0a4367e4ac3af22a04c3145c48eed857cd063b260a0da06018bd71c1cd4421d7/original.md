```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.PowerCone) where {T}
```

projection of vector `v` on the dual power cone i.e. `K_pow^* = {(u,v,w) | (u/a)^a * (v/(1-a))^(1-a) >= |w|, u>=0, v>=0}`.

References:

  * [Differential properties of Euclidean projection onto power cone]

(https://link.springer.com/article/10.1007/s00186-015-0514-0), Prop 2.2
