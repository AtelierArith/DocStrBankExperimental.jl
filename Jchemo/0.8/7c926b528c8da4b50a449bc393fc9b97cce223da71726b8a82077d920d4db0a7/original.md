```
out(x)
```

Return if elements of a vector are strictly outside of a given range.

  * `x` : Univariate data.
  * `y` : Univariate data on which is computed the range (min, max).

Return a BitVector.

## Examples

```julia
using Jchemo

x = [-200.; -100; -1; 0; 1; 200]
out(x, [-1; .2; 1])
out(x, (-1, 1))
```
