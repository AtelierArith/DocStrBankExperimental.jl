```
set_parameters!(ds::DynamicalSystem, p = initial_parameters(ds))
```

Set the parameter values in the [`current_parameters`](@ref)`(ds)` to match those in `p`. This is done as an in-place overwrite by looping over the keys of `p` hence `p` can be an arbitrary container mapping parameter indices to values (such as a `Vector{Real}`, `Vector{Pair}`, or `AbstractDict`).

The keys of `p` must be valid keys that can be given to [`set_parameter!`](@ref).
