```
mweight(x::Vector)
```

Return an object of type `Weight` containing vector `w = x / sum(x)` (if ad'hoc building,      `w` must sum to 1).

## Examples

```julia
using Jchemo

x = rand(10)
w = mweight(x)
sum(w.w)
```
