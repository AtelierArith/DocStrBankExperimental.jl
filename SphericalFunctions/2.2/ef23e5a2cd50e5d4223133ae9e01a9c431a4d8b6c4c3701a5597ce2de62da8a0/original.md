```
D_matrices(R, ℓₘₐₓ)
D_matrices(α, β, γ, ℓₘₐₓ)
```

Compute Wigner's 𝔇 matrices $\mathfrak{D}^{(\ell)}_{m',m}(\beta)$ for all $\ell \leq \ell_\mathrm{max}$.

See [`D_matrices!`](@ref) for details about the input and output values.

This function only appropriate when you need to evaluate the matrices for a single value of `R` or `α, β, γ` because it allocates large arrays and performs many calculations that could be reused.  If you need to evaluate the matrices for many values of `R` or `α, β, γ`, you should pre-allocate the storage with [`D_prep`](@ref), and then call [`D_matrices!`](@ref) with the result instead.
