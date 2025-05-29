```
recod_catbyint(x; start = 1)
```

Recode a categorical variable to integers.

  * `x` : Categorical variable (n) to replace.
  * `start` : Integer labelling the first categorical level in `x`.

The integers returned by the function correspond to the sorted  levels of `x`, see examples.

## Examples

```julia
using Jchemo

x = ["b", "a", "b"]
mlev(x)   
[x recod_catbyint(x)]
recod_catbyint(x; start = 0)

recod_catbyint([25, 1, 25])
```
