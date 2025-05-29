```
log(M::CholeskySpace, X, p, q)
```

Compute the logarithmic map on the [`CholeskySpace`](@ref) `M` for the geodesic emanating from the lower triangular matrix with positive diagonal `p` towards `q`. The formula reads

$$
\log_p q = ⌊ p ⌋ - ⌊ q ⌋ + \operatorname{diag}(p)\log\bigl(\operatorname{diag}(q)\operatorname{diag}(p)^{-1}\bigr),
$$

where $⌊⋅⌋$ denotes the strictly lower triangular matrix, and $\operatorname{diag}$ extracts the diagonal matrix.
