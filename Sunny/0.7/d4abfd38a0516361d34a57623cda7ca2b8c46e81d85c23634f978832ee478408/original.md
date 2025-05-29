```
ssf_custom_bm(f, sys::System; u, v, apply_g=true, formfactors=nothing)
```

Specify measurement of the spin structure factor with a custom contraction function `f`. The interface is identical to [`ssf_custom`](@ref) except that `f` here receives momentum $𝐪$ and the 3×3 structure factor data $\mathcal{S}^{αβ}(𝐪, ω)$ in the basis of the Blume-Maleev axis system. The wavevectors `u` and `v`, provided in reciprocal lattice units, will be used to define the scattering plane. In global Cartesian coordinates, the three orthonormal BM axes `(e1, e2, e3)` are defined as follows:

```julia
e3 = normalize(u × v)  # normal to the scattering plane (u, v)
e1 = normalize(q)      # momentum transfer q within scattering plane
e2 = normalize(e3 × q) # perpendicular to q and in the scattering plane
```

# Example

```julia
# Measure imaginary part of S²³ - S³² in the Blume-Maleev axis system for
# the scattering plane [0, K, L].
measure = ssf_custom_bm(sys; u=[0, 1, 0], v=[0, 0, 1]) do q, ssf
    imag(ssf[2,3] - ssf[3,2])
end
```
