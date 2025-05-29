```
mlev(x)
```

Return the sorted levels of a vector or a dataset. 

## Examples

```julia
using Jchemo

x = rand(["a";"b";"c"], 20)
lev = mlev(x)
nlev = length(lev)

X = reshape(x, 5, 4)
mlev(X)

df = DataFrame(g1 = rand(1:2, n), g2 = rand(["a"; "c"], n))
mlev(df)
```
