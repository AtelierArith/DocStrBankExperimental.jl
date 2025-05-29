```
groupparams(m::AbstractModel, cols::Symbol...)
```

Groups parameters in `m` hierarchically according to `cols`. A `Symbol` constructor must be defined for the value type of each parameter field (e.g. `String`, `Symbol`, and `Int` would all be valid by default). The returned value is a nested named tuple where the hierachical order follows the order of `cols`.

For example, we could group parameters first by component name, then by field name:

# Examples

```julia-repl
julia> groupparams(Model((a=Param(1.0), b=Param(2.0))), :component, :fieldname)
(NamedTuple = (a = ..., b = ...),)
```
