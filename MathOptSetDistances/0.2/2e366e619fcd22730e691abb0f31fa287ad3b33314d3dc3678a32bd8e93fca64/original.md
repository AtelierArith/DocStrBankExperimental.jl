```
projection_gradient_on_set(d::DefaultDistance, v::AbstractVector{T}, ::MOI.DualPowerCone) where {T}
```

derivative of projection of vector `v` on the dual power cone i.e. `K_pow^* = {(u,v,w) | (u/a)^a * (v/(1-a))^(1-a) >= |w|, u>=0, v>=0}`.

References:

  * [Differential properties of Euclidean projection onto power cone]

(https://link.springer.com/article/10.1007/s00186-015-0514-0), Theorem 3.1
