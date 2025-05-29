```julia
configuration(state)

```

Return the configuration vector $q$.

Note that this returns a reference to the underlying data in `state`. The user is responsible for calling [`setdirty!`](@ref) after modifying this vector to ensure that dependent cache variables are invalidated.
