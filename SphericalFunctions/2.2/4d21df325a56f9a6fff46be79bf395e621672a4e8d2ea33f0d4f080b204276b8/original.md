```
D_matrices!(D_storage, R)
D_matrices!(D_storage, α, β, γ)
D_matrices!(D, R, ℓₘₐₓ)
D_matrices!(D, α, β, γ, ℓₘₐₓ)
```

Compute Wigner's 𝔇 matrices $\mathfrak{D}^{(\ell)}_{m',m}(\beta)$ for all $\ell \leq \ell_\mathrm{max}$.

In all cases, the result is returned in a 1-dimensional array ordered as

```
[
    𝔇ˡₘₚ,ₘ(R)
    for ℓ ∈ 0:ℓₘₐₓ
    for mp ∈ -ℓ:ℓ
    for m ∈ -ℓ:ℓ
]
```

When the first argument is `D`, it will be modified, so it must be at least as large as that array. When the first argument is `D_storage`, it should be the quantity returned by [`D_prep`](@ref), and the result will be written into the `D` field of that tuple.  Both of these options — especially the latter — reduce the number of allocations needed on each call to the corresponding functions, which should increase the speed significantly.  Note that the `D` or `D_storage` arguments must have types compatible with the type of `R` or `α, β, γ`.

!!! warn
    When using the `D_storage` argument (which is recommended), the returned quantity `D` will be an alias of `D_storage[1]`.  If you want to retain that data after the next call to [`D_matrices!`](@ref), you should copy it with `copy(D)`.


The `α, β, γ` arguments are Euler angles as described in the documentation of [`Quaternionic.from_euler_angles`](https://moble.github.io/Quaternionic.jl/dev/manual/#Quaternionic.from_euler_angles-Tuple{Any,%20Any,%20Any}).

See also [`D_matrices`](@ref) for a simpler function call when you only need to evaluate the matrices for a single value of `R` or `α, β, γ`.

# Examples

```julia
using Quaternionic, SphericalFunctions
ℓₘₐₓ = 8
T = Float64
R = Rotor{T}(1, 2, 3, 4)  # Will be normalized automatically
D_storage = D_prep(ℓₘₐₓ, T)
D = D_matrices!(D_storage, R)
```
