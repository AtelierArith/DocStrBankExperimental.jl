```
show_backend_summary(io::IO, model::GenericModel)
```

Print a summary of the optimizer backing `model`.

## Extensions

`AbstractModel`s should implement this method.

## Example

```jldoctest
julia> model = Model();

julia> show_backend_summary(stdout, model)
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
