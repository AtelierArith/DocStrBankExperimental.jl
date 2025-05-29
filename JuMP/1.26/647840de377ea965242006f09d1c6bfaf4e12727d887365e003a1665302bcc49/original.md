```
struct NoOptimizer <: Exception end
```

An error thrown when no optimizer is set and one is required.

The optimizer can be provided to the [`Model`](@ref) constructor or by calling [`set_optimizer`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> optimize!(model)
ERROR: NoOptimizer()
Stacktrace:
[...]
```
