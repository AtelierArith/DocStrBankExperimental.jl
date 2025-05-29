```
ModelMode
```

An enum to describe the state of the CachingOptimizer inside a JuMP model.

See also: [`mode`](@ref).

## Values

Possible values are:

  * [`AUTOMATIC`]: `moi_backend` field holds a CachingOptimizer in AUTOMATIC mode.
  * [`MANUAL`]: `moi_backend` field holds a CachingOptimizer in MANUAL mode.
  * [`DIRECT`]: `moi_backend` field holds an AbstractOptimizer. No extra copy of the model is stored. The `moi_backend` must support `add_constraint` etc.
