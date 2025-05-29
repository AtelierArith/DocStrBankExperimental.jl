```
varv(x)
varv(x, weights::Weight)
```

Compute the uncorrected variance of a vector.

  * `x` : A vector (n).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

## Examples

```julia
using Jchemo

n = 1000
x = rand(n)
w = mweight(rand(n))

varv(x)
varv(x, w)
```
