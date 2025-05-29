```
tunable_parameters(sys, p = parameters(sys); default=false)
```

Get all parameters of `sys` that are marked as `tunable`.

Keyword argument `default` indicates whether variables without `tunable` metadata are to be considered tunable or not.

Create a tunable parameter by

```
@parameters u [tunable=true]
```

See also [`getbounds`](@ref), [`istunable`](@ref)
