```
length(at::AliasTable)
```

Get the number of weights that `at` was constructed with, including trailing zeros.

# Example

```jldoctest
julia> length(AliasTable([1, 3, 0]))
3
```
