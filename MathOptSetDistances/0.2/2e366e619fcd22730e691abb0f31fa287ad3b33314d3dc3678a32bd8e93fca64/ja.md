```
projection_gradient_on_set(d::DefaultDistance, v::AbstractVector{T}, ::MOI.DualPowerCone) where {T}
```

ベクトル `v` の双対パワーコーンへの射影の導関数、すなわち `K_pow^* = {(u,v,w) | (u/a)^a * (v/(1-a))^(1-a) >= |w|, u>=0, v>=0}`。

参考文献:

  * [Differential properties of Euclidean projection onto power cone]

(https://link.springer.com/article/10.1007/s00186-015-0514-0), 定理 3.1
