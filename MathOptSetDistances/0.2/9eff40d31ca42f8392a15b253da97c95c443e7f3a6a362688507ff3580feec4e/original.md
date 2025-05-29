```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.DualExponentialCone) where {T}
```

derivative of projection of vector `v` on the dual exponential cone, i.e. `Kexp^* = {(u,v,w) | u < 0, -u*exp(v/u) <= exp(1)*w } U {(u,v,w)| u == 0, v >= 0, w >= 0}`.

References:

  * [Solution Refinement at Regular Points of Conic Problems]

(https://stanford.edu/~boyd/papers/cone*prog*refine.html) by Enzo Busseti, Walaa M. Moursi, and Stephen Boyd
