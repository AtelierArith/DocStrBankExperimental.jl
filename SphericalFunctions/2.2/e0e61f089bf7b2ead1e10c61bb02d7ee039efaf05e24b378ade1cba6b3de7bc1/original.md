```
sYlm_values(R, ℓₘₐₓ, spin)
sYlm_values(θ, ϕ, ℓₘₐₓ, spin)
```

Compute values of the spin-weighted spherical harmonic ${}_{s}Y_{\ell, m}(R)$ for all $\ell \leq \ell_\mathrm{max}$.

See [`sYlm_values!`](@ref) for details about the input and output values.

This function only appropriate when you need to evaluate the ${}_{s}Y_{\ell, m}$ for a single value of `R` or `θ, ϕ` because it allocates large arrays and performs many calculations that could be reused.  If you need to evaluate the matrices for many values of `R` or `θ, ϕ`, you should pre-allocate the storage with [`sYlm_prep`](@ref), and then call [`sYlm_values!`](@ref) with the result instead.
