```
get_rho(psi::AbstractVector{T}; S::Real=1/2, LA::Int=0)
```

return the reduced density matrix ρ with subsystem size `LA` default to L÷2 if unspecified. Here we are considering the case of non-restricted Hilbert space, i.e. dimension of `psi` is base^L.

For the case of restricted Hilbert space, such as Mz sector of spin system of PXP model, current naive method can be quite slow. In this case, use the alternative method.

# Example

```julia-reply
julia> rho = get_rho(psi; S=1)
julia> rho = get_rho(psi; LA=4)
julia> rho = get_rho(psi; S=1/2, LA=4)
```
