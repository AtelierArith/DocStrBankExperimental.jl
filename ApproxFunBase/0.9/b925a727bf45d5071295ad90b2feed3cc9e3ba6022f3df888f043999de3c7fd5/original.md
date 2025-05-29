```
LowRankFun(f, space::TensorSpace)
```

Return an approximation to a bivariate function in a low-rank form

$$
f(x,y) = \sum_i \sigma_i \phi_i(x) \psi_i(y)
$$

where $\sigma_i$ represent the highest singular values, and $\phi_i(x)$ and $\psi_i(y)$ are orthogonal bases. The summation is truncated after an acceptable tolerance is reached.

# Examples

```jldoctest
julia> f = (x,y) -> x^2 * y^3;

julia> L = LowRankFun(f, Chebyshev() ⊗ Chebyshev());

julia> L(0.1, 0.2) ≈ f(0.1, 0.2)
true
```
