```
list(Q, n::Integer)
```

Create a Vector `{Q}(undef, n)`.

`isassigned(object, i)` can be used to check if cell i is empty.

## Examples

```julia
using Jchemo

list(Float64, 5)
list(Array{Float64}, 5)
list(Matrix{Int}, 5)
```
