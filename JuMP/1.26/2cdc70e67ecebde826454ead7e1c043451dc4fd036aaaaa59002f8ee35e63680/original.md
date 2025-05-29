```
struct OptimizeNotCalled <: Exception end
```

An error thrown when a result attribute cannot be queried before [`optimize!`](@ref) is called.

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> objective_value(model)
ERROR: OptimizeNotCalled()
Stacktrace:
[...]
```
