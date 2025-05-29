```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.DualExponentialCone) where {T}
```

projection of vector `v` on the dual exponential cone i.e. `Kexp^* = {(u,v,w) | u < 0, -u*exp(v/u) <= ew } U {(u,v,w)| u == 0, v >= 0, w >= 0}`.

References:

  * [Proximal Algorithms, 6.3.4](https://web.stanford.edu/~boyd/papers/pdf/prox_algs.pdf)

by Neal Parikh and Stephen Boyd.

  * [Projection, presolve in MOSEK: exponential, and power cones](https://docs.mosek.com/slides/2018/ismp2018/ismp-friberg.pdf)

by Henrik Friberg
