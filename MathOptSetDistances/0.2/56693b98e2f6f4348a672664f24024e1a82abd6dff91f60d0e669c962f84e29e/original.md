```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.ExponentialCone) where {T}
```

projection of vector `v` on closure of the exponential cone i.e. `cl(Kexp) = {(x,y,z) | y e^(x/y) <= z, y>0 } U {(x,y,z)| x <= 0, y = 0, z >= 0}`.

References:

  * [Proximal Algorithms, 6.3.4](https://web.stanford.edu/~boyd/papers/pdf/prox_algs.pdf)

by Neal Parikh and Stephen Boyd.

  * [Projection, presolve in MOSEK: exponential, and power cones]

(https://docs.mosek.com/slides/2018/ismp2018/ismp-friberg.pdf) by Henrik Friberg

  * [Projection onto the exponential cone: a univariate root-finding problem]

(https://docs.mosek.com/whitepapers/expcone-proj.pdf) by Henrik Friberg 2021
