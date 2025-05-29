```
tunable_parameters(sys, p = parameters(sys; initial_parameters = true); default=true)
```

Get all parameters of `sys` that are marked as `tunable`.

Keyword argument `default` indicates whether variables without `tunable` metadata are to be considered tunable or not.

Create a tunable parameter by

```
@parameters u [tunable=true]
```

For systems created with `split = true` (the default) and `default = true` passed to this function, the order of parameters returned is the order in which they are stored in the tunables portion of `MTKParameters`. Note that array variables will not be scalarized. To obtain the flattened representation of the tunables portion, call `Symbolics.scalarize(tunable_parameters(sys))` and concatenate the resulting arrays.

See also [`getbounds`](@ref), [`istunable`](@ref), [`MTKParameters`](@ref), [`complete`](@ref)
