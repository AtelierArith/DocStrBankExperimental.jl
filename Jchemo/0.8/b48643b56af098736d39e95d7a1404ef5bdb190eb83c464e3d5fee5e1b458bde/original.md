```
normv(x)
normv(x, weights::Weight)
```

Compute the norm of a vector.

  * `x` : A vector (n).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

The weighted norm of vector `x` is computed by:

  * sqrt(x' * D * x), where D is the diagonal matrix of vector `weights.w`.

## References

@gdkrmr, https://discourse.julialang.org/t/julian-way-to-write-this-code/119348/17

@Stevengj,  https://discourse.julialang.org/t/interesting-post-about-simd-dot-product-and-cosine-similarity/123282.

## Examples

```julia
using Jchemo

n = 1000
x = rand(n)
w = mweight(ones(n))

normv(x)
sqrt(n) * normv(x, w)
```
