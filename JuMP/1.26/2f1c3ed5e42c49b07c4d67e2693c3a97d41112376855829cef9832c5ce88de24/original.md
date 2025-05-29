```
result_count(model::GenericModel)
```

Return the number of results available to query after a call to [`optimize!`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> result_count(model)
0
```
