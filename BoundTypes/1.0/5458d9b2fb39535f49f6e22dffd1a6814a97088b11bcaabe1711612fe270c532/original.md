```
bound_type(x) -> type
```

Returns the type of the internal object of `x`.

## Examples

```jldoctest
julia> bound_type(NumberPositive{Float64}(1.0))
Float64

julia> bound_type(NumberLess{NumberGreater{Int64,2},8}(6))
Int64
```
