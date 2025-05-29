```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.PowerCone; [max_iters_newton = 100, max_iters_bisection = 1000]) where {T}
```

ベクトル `v` のパワーコーンへの射影、すなわち `K = {(x,y,z) | x^a * y^(1-a) >= |z|, x>=0, y>=0}`。

参考文献:

  * [Differential properties of Euclidean projection onto power cone]

(https://link.springer.com/article/10.1007/s00186-015-0514-0), Prop 2.2
