```
projection_gradient_on_set(d::DefaultDistance, v::AbstractVector{T}, ::MOI.PowerCone) where {T}
```

derivative of projection of vector `v` on the power cone i.e. `K = {(x,y,z) | x^a * y^(1-a) >= |z|, x>=0, y>=0}`.

References:

  * [Differential properties of Euclidean projection onto power cone]

(https://link.springer.com/article/10.1007/s00186-015-0514-0), Theorem 3.1
