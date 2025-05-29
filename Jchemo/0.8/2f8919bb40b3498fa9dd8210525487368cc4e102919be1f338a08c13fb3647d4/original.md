```
aggsumv(x::Vector, y::Union{Vector, BitVector})
```

Compute sub-total sums by class of a categorical variable.

  * `x` : A quantitative variable to sum (n)
  * `y` : A categorical variable (n) (class membership).

## Examples

```julia
using Jchemo

x = rand(1000)
y = vcat(rand(["a" ; "c"], 900), repeat(["b"], 100))
aggsumv(x, y)
```
