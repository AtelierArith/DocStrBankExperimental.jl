```
box_approximation(lm::LinearMap{N, <:AbstractHyperrectangle}) where {N}
```

Return a tight overapproximation of the linear map of a hyperrectangular set using a hyperrectangle.

### Input

  * `lm`– linear map of a hyperrectangular set

### Output

A hyperrectangle.

### Algorithm

If `c` and `r` denote the center and vector radius of a hyperrectangle `H`, a tight hyperrectangular overapproximation of `M * H` is obtained by transforming `c ↦ M*c` and `r ↦ abs.(M) * r`, where `abs.(⋅)` denotes the element-wise absolute-value operator.
