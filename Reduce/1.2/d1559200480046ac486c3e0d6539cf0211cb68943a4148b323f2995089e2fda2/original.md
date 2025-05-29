```
multiplicities(::Bool)
```

If you want the multiplicities explicitly displayed, the switch `multiplicities` can be turned on. For example

```Julia
julia> Algebra.on(:multiplicities); Algebra.solve(:(x^2==2x-1),:x)
```

yields the result

```Julia
(:(x = 1), :(x = 1))
```
