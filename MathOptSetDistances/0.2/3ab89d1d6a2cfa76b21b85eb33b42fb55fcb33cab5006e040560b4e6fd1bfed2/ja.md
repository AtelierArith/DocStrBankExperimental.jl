```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.DualExponentialCone) where {T}
```

ベクトル `v` の双対指数円錐への射影、すなわち `Kexp^* = {(u,v,w) | u < 0, -u*exp(v/u) <= ew } U {(u,v,w)| u == 0, v >= 0, w >= 0}`。

参考文献:

  * [Proximal Algorithms, 6.3.4](https://web.stanford.edu/~boyd/papers/pdf/prox_algs.pdf)

Neal Parikh と Stephen Boyd による。

  * [Projection, presolve in MOSEK: exponential, and power cones](https://docs.mosek.com/slides/2018/ismp2018/ismp-friberg.pdf)

Henrik Friberg による。
