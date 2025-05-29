```
exp(M::CholeskySpace, p, X)
```

Compute the exponential map on the [`CholeskySpace`](@ref) `M` emanating from the lower triangular matrix with positive diagonal `p` towards the lower triangular matrix `X` The formula reads

$$
\exp_p X = ⌊ p ⌋ + ⌊ X ⌋ + \operatorname{diag}(p)
\operatorname{diag}(p)\exp\bigl( \operatorname{diag}(X)\operatorname{diag}(p)^{-1}\bigr),
$$

where $⌊⋅⌋$ denotes the strictly lower triangular matrix, and $\operatorname{diag}$ extracts the diagonal matrix.
