```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.ExponentialCone) where {T}
```

derivative of projection of vector `v` on closure of the exponential cone, i.e. `cl(Kexp) = {(x,y,z) | y e^(x/y) <= z, y>0 } U {(x,y,z)| x <= 0, y = 0, z >= 0}`.

References:

  * [Solution Refinement at Regular Points of Conic Problems](https://stanford.edu/~boyd/papers/cone_prog_refine.html)

by Enzo Busseti, Walaa M. Moursi, and Stephen Boyd
