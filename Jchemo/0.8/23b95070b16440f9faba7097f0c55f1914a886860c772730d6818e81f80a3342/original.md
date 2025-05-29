```
cosv(x, y)
```

Compute uncorrected covariance between two vectors.

  * `x` : vector (n).
  * `y` : vector (n).

## References

@Stevengj,  https://discourse.julialang.org/t/interesting-post-about-simd-dot-product-and-cosine-similarity/123282.

## Examples

```julia
using Jchemo

n = 5
x = rand(n)
y = rand(n)

covv(x, y)
```
