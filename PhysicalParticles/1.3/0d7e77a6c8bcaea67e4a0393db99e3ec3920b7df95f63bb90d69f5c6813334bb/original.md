```
function average(data, symbol::Symbol)
```

Average on field `symbol` of elements in an array or dict of arrays

## Examples

```jl
a = rand(PVector{Float64}, 5)
average(a, :x)
```
