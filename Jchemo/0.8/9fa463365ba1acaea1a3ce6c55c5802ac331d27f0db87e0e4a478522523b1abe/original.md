```
tabdupl(x)
```

Tabulate duplicated values in a vector.

  * `x` : Categorical variable.

## Examples

```julia
using Jchemo

x = ["a", "b", "c", "a", "b", "b"]
tab(x)
res = tabdupl(x)
res.keys
res.vals
```
