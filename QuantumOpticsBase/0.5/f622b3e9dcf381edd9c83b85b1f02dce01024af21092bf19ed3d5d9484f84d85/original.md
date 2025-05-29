```
squeeze([T=ComplexF64,] b::FockBasis, z)
```

Squeezing operator $S(z)=\exp{\left(\frac{z^*\hat{a}^2-z\hat{a}^{\dagger2}}{2}\right)}$ for the specified Fock space with optional data type `T`, computed as the matrix exponential of finite-dimensional (truncated) creation and annihilation operators.
