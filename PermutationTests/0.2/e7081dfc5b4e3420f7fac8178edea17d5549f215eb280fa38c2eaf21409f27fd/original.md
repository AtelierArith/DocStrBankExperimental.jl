```julia
function dispersion(x::UniData, mean::Real)
```

Sum of squared deviations of the elements in `x` around `mean`.

`mean` must be provided and must be a real number.

*Examples*

```julia
using PermutationTests
x=randn(10)
d=dispersion(x, μ(x))
```
