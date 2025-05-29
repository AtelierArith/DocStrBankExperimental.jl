```
meanv(x)
meanv(x, weights::Weight)
```

Compute the mean of a vector. 

  * `x` : A vector (n).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

## Examples

```julia
using Jchemo

n = 100
x = rand(n)
w = mweight(rand(n)) 

meanv(x)
meanv(x, w)
```
