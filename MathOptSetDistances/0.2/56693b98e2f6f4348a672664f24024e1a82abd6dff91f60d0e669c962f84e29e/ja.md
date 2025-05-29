```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.ExponentialCone) where {T}
```

ベクトル `v` の指数コーンの閉包への射影、すなわち `cl(Kexp) = {(x,y,z) | y e^(x/y) <= z, y>0 } U {(x,y,z)| x <= 0, y = 0, z >= 0}`。

参考文献：

  * [Proximal Algorithms, 6.3.4](https://web.stanford.edu/~boyd/papers/pdf/prox_algs.pdf)

Neal Parikh と Stephen Boyd による。

  * [Projection, presolve in MOSEK: exponential, and power cones]

(https://docs.mosek.com/slides/2018/ismp2018/ismp-friberg.pdf) Henrik Friberg による

  * [Projection onto the exponential cone: a univariate root-finding problem]

(https://docs.mosek.com/whitepapers/expcone-proj.pdf) Henrik Friberg 2021 による
