```
sYlm_values!(sYlm_storage, R, spin)
sYlm_values!(sYlm_storage, θ, ϕ, spin)
sYlm_values!(sYlm, R, ℓₘₐₓ, spin)
sYlm_values!(sYlm, θ, ϕ, ℓₘₐₓ, spin)
```

Compute values of the spin-weighted spherical harmonic ${}_{s}Y_{\ell, m}(R)$ for all $\ell \leq \ell_\mathrm{max}$.

The spherical harmonics of spin weight $s$ are related to Wigner's $\mathfrak{D}$ matrix as

$$
\begin{aligned}
{}_{s}Y_{\ell, m}(R)
  &= (-1)^s \sqrt{\frac{2\ell+1}{4\pi}} \mathfrak{D}^{(\ell)}_{m, -s}(R) \\
  &= (-1)^s \sqrt{\frac{2\ell+1}{4\pi}} \bar{\mathfrak{D}}^{(\ell)}_{-s, m}(\bar{R}).
\end{aligned}
$$

In all cases, the result is returned in a 1-dimensional array ordered as

```
[
    ₛYₗₘ(R)
    for ℓ ∈ 0:ℓₘₐₓ
    for m ∈ -ℓ:ℓ
]
```

When the first argument is `Y`, it will be modified, so it must be at least as large as that array. When the first argument is `sYlm_storage`, it should be the quantity returned by [`sYlm_prep`](@ref), and the result will be written into the `Y` field of that tuple.  Both of these options — especially the latter — reduce the number of allocations needed on each call to the corresponding functions, which should increase the speed significantly.  Note that the `Y` or `sYlm_storage` arguments must have types compatible with the type of `R` or `θ, ϕ`.

!!! warn
    When using the `sYlm_storage` argument (which is recommended), the returned quantity `sYlm` will be an alias of `sYlm_storage[1]`.  If you want to retain that data after the next call to [`sYlm_values!`](@ref), you should copy it with `copy(sYlm)`.


The `θ, ϕ` arguments are spherical coordinates as described in the documentation of [`Quaternionic.from_spherical_coordinates`](https://moble.github.io/Quaternionic.jl/dev/manual/#Quaternionic.from_spherical_coordinates-Tuple{Any,%20Any}).

See also [`sYlm_values`](@ref) for a simpler function call when you only need to evaluate the ${}_{s}Y_{\ell, m}$ for a single value of `R` or `θ, ϕ`.

# Examples

```julia
using Quaternionic, SphericalFunctions
spin = -2
ℓₘₐₓ = 8
T = Float64
R = Rotor{T}(1, 2, 3, 4)  # Will be normalized automatically
sYlm_storage = sYlm_prep(ℓₘₐₓ, spin, T)
sYlm = sYlm_values!(sYlm_storage, R, spin)
```
