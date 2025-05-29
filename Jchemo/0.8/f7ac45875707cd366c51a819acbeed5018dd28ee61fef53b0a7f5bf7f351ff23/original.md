```
sumv(x)
sumv(x, weights::Weight)
```

Compute the sum of a vector. 

  * `x` : A vector (n).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

## Examples

```julia
using Jchemo

n = 100
x = rand(n)
w = mweight(rand(n)) 

sumv(x)
sumv(x, w)
```
