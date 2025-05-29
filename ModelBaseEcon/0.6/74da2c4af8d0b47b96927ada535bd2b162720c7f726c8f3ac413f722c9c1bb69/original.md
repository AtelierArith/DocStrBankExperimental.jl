```
linearized(model::Model; <arguments>)
```

Create a new model that is the linear approximation of the given model about its steady state.

### Keyword arguments

  * `sstate` - linearize about the provided steady state solution
  * `deviation`::Bool - whether or not the linearized model will tread data passed

to is as deviation from the steady state

See also: [`linearize!`](@ref) and [`with_linearized`](@ref)
