```
with_linearized(F::Function, model::Model; <arguments>)
```

Apply the given function on a new model that is the linear approximation  of the given model about its steady state.  This is meant to be used with the `do` syntax, as in the example below.

### Keyword arguments

  * `sstate` - linearize about the provided steady state solution
  * `deviation`::Bool - whether or not the linearized model will tread data passed

to is as deviation from the steady state

See also: [`linearize!`](@ref) and [`with_linearized`](@ref)

### Example

```julia
with_linearized(m) do lm
    # do something awesome with linearized model `lm`
end
# model `m` is still non-linear.
```
