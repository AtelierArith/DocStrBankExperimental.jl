```
ssf_custom(f, sys::System; apply_g=true, formfactors=nothing)
```

Specify measurement of the spin structure factor with a custom contraction function `f`. This function accepts a wavevector $𝐪$ in global Cartesian coordinates, and a 3×3 matrix with structure factor intensity components $\mathcal{S}^{αβ}(𝐪,ω)$. Indices $(α, β)$ denote dipole components in global coordinates. The return value of `f` can be any number or `isbits` type. With specific choices of `f`, one can obtain measurements such as defined in [`ssf_perp`](@ref) and [`ssf_trace`](@ref).

By default, the g-factor or tensor is applied at each site, such that the structure factor components are correlations between the magnetic moment operators. Set `apply_g=false` to measure correlations between the bare spin operators.

The optional `formfactors` comprise a list of pairs `[i1 => FormFactor(...), i2 => ...]`, where `i1, i2, ...` are a complete set of symmetry-distinct atoms, and each [`FormFactor`](@ref) implements $𝐪$-space attenuation for the given atom.

Intended for use with [`SpinWaveTheory`](@ref) and instances of [`SampledCorrelations`](@ref).

# Examples

```julia
# Measure all structure factor components Sᵅᵝ as a 3×3 matrix
measure = ssf_custom((q, ssf) -> ssf, sys)

# Measure the structure factor trace Sᵅᵅ
measure = ssf_custom((q, ssf) -> real(ssf[1, 1] + ssf[2, 2] + ssf[3, 3]), sys)
```

See also the Sunny documentation on [Structure Factor Conventions](@ref).
