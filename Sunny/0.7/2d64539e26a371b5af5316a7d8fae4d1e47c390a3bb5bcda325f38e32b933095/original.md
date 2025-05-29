```
ssf_perp(sys::System; apply_g=true, formfactors=nothing)
```

Specify measurement of the spin structure factor with contraction by $(I-𝐪⊗𝐪/q^2)$. The contracted value provides an estimate of unpolarized scattering intensity. In the singular limit $𝐪 → 0$, the contraction matrix is replaced by its rotational average, $(2/3) I$.

This function is a special case of [`ssf_custom`](@ref).

# Example

```julia
# Select Co²⁺ form factor for atom 1 and its symmetry equivalents
formfactors = [1 => FormFactor("Co2")]
ssf_perp(sys; formfactors)
```
