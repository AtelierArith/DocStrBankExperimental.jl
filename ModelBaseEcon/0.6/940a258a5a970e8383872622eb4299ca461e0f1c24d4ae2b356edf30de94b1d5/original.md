```
linearize!(model::Model; <keyword arguments>)
```

Transform model into its linear approximation about its steady state.

### Keyword arguments

  * `sstate` - linearize about the provided steady state solution
  * `deviation`::Bool - whether or not the linearized model will treat data passed to it as deviation from the steady state

See also: [`linearized`](@ref) and [`with_linearized`](@ref)
