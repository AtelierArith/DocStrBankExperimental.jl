```
istunable(x, default = false)
```

Determine whether symbolic variable `x` is marked as a tunable for an automatic tuning algorithm.

`default` indicates whether variables without `tunable` metadata are to be considered tunable or not.

Create a tunable parameter by

```
@parameters u [tunable=true]
```

See also [`tunable_parameters`](@ref), [`getbounds`](@ref)
