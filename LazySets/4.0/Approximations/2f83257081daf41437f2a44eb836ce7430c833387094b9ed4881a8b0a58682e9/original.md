```
box_approximation(am::AbstractAffineMap{N, <:AbstractHyperrectangle}) where {N}
```

Overapproximate the affine map of a hyperrectangular set by a tight hyperrectangle.

### Input

  * `am` – affine map of a hyperrectangular set

### Output

A hyperrectangle.

### Algorithm

If `c` and `r` denote the center and vector radius of a hyperrectangle `H` and `v` is the translation vector, a tight hyperrectangular overapproximation of `M * H + v` is obtained by transforming `c ↦ M*c+v` and `r ↦ abs.(M) * r`, where `abs.(⋅)` denotes the element-wise absolute-value operator.
