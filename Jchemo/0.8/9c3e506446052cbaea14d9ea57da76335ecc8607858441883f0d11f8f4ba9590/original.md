```
recod_catbylev(x, lev)
```

Recode a categorical variable to levels.

  * `x` : Variable (n) to replace.
  * `lev` : Vector containing the categorical levels.

The ith sorted level in `x` is replaced by the ith sorted level in `lev`,  see examples.

*Warning*: `x` and `lev` must contain the same number of levels.

## Examples

```julia
using Jchemo

x = [10 ; 4 ; 3 ; 3 ; 4 ; 4]
lev = ["B" ; "C" ; "AA" ; "AA"]
mlev(x)
mlev(lev)
[x recod_catbylev(x, lev)]
xstr = string.(x)
[xstr recod_catbylev(xstr, lev)]

lev = [3; 0; 0; -1]
mlev(x)
mlev(lev)
[x recod_catbylev(x, lev)]
```
