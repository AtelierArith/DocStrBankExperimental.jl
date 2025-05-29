```julia
mutable struct DynamicsResult{T, M}
```

Stores variables related to the dynamics of a `Mechanism`, e.g. the `Mechanism`'s mass matrix and joint acceleration vector.

Type parameters:

  * `T`: the scalar type of the dynamics-related variables.
  * `M`: the scalar type of the `Mechanism`.
