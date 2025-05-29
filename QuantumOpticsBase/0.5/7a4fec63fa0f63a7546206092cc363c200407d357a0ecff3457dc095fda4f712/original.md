```
displace([T=ComplexF64,] b::FockBasis, alpha)
```

Displacement operator $D(α)=\exp{\left(α\hat{a}^\dagger-α^*\hat{a}\right)}$ for the specified Fock space with optional data type `T`, computed as the matrix exponential of finite-dimensional (truncated) creation and annihilation operators.
