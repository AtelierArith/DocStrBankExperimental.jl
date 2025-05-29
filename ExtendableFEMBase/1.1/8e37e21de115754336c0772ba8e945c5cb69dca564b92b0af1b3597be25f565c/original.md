```julia
abstract type Curl2D <: ??
```

evaluates the curl of some two-dimensional vector field, i.e. Curl2D((u1,u2)) = du2/dx1 - du1/dx2
