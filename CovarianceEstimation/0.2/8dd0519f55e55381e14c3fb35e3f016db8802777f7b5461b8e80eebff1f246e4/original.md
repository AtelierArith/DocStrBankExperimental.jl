```
NormLossCov(norm::Symbol, pivotidx::Int)
```

Specify a loss function for which the estimated covariance will be optimal. `norm` is one of `:L1`, `:L2`, or `:Linf`, and `pivotidx` is an integer from 1 to 7, as specified in Table 1 (p. 1755) of Donoho et al. (2018). In the table below, `A` and `B` are the target and sample covariances, respectively, and the loss function is the specified norm on the quantity in the `pivot` column:

| `pivotidx` |                      `pivot` |                   Notes |
| ----------:| ----------------------------:| -----------------------:|
|          1 |                      `A - B` |                         |
|          2 |                  `A⁻¹ - B⁻¹` |                         |
|          3 |                  `A⁻¹ B - I` | Not available for `:L1` |
|          4 |                  `B⁻¹ A - I` | Not available for `:L1` |
|          5 |         `A⁻¹ B + B⁻¹ A - 2I` |           Not supported |
|          6 |  `sqrt(A) \ B / sqrt(A) - I` |                         |
|          7 | `log(sqrt(A) \ B / sqrt(A))` |           Not supported |

See also [`StatLossCov`](@ref).

Reference:     Donoho, D.L., Gavish, M. and Johnstone, I.M., 2018.     Optimal shrinkage of eigenvalues in the spiked covariance model. Annals of statistics, 46(4), p.1742.
