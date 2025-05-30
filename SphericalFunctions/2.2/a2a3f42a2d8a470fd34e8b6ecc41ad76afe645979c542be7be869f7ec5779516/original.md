```
d_matrices(β, ℓₘₐₓ)
d_matrices(expiβ, ℓₘₐₓ)
```

Compute Wigner's $d^{(\ell)}$ matrices with elements $d^{(\ell)}_{m',m}(\beta)$ for all $\ell \leq \ell_\mathrm{max}$.  The $d$ matrices are sometimes called the "reduced" Wigner matrices, in contrast to the full $\mathfrak{D}$ matrices.

See [`d_matrices!`](@ref) for details about the input and output values.

This function only appropriate when you need to evaluate the matrices for a single value of `β` or `expiβ` because it allocates large arrays and performs many calculations that could be reused.  If you need to evaluate the matrices for many values of `β` or `expiβ`, you should pre-allocate the storage with [`d_prep`](@ref), and then call [`d_matrices!`](@ref) with the result instead.
