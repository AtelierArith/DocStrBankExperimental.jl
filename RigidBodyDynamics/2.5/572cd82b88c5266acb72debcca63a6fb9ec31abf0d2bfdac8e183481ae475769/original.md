```julia
velocity(state)

```

Return the velocity vector $v$.

Note that this function returns a read-write reference to a field in `state`. The user is responsible for calling [`setdirty!`](@ref) after modifying this vector to ensure that dependent cache variables are invalidated.
