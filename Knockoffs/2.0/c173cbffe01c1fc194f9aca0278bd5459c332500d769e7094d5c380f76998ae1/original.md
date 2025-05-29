```
ipad(X::Matrix; [r_method], [m])
```

Generates knockoffs based on intertwined probabilitistic factors decoupling (IPAD). This assumes that `X` can be factored as `X = FΛ' + E` where `F` is a `n × r` random matrix of latent factors, `Λ` are factor loadings, and `E` are residual errors. When this assumption is met, FDR can be controlled with no power loss when applying the knockoff procedure. Internally, we need to compute an eigenfactorization for a `n × n` matrix. This is often faster than standard model-X knockoffs which requires solving `p`-dimensional convex optimization problem.

# Inputs

  * `X`: A `n × p` numeric matrix, each row is a sample, and each column is covariate.
  * `r_method`: Method used for estimating `r`, the number of latent factors.    Choices include `:er` (default), `:gr`, or `:ve`
  * `m`: Number of (simultaneous) knockoffs per variable to generate, default `m=1`

# References

  * Fan, Y., Lv, J., Sharifvaghefi, M. and Uematsu, Y., 2020. IPAD: stable interpretable forecasting with knockoffs inference. Journal of the American Statistical Association, 115(532), pp.1822-1834.
  * Bai, J., 2003. Inferential theory for factor models of large dimensions. Econometrica, 71(1), pp.135-171.
  * Ahn, S.C. and Horenstein, A.R., 2013. Eigenvalue ratio test for the number of factors. Econometrica, 81(3), pp.1203-1227.
