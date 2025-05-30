```
d_matrices!(d_storage, β)
d_matrices!(d_storage, expiβ)
d_matrices!(d, β, ℓₘₐₓ)
d_matrices!(d, expiβ, ℓₘₐₓ)
```

Compute Wigner's $d^{(\ell)}$ matrices with elements $d^{(\ell)}_{m',m}(\beta)$ for all $\ell \leq \ell_\mathrm{max}$.  The $d$ matrices are sometimes called the "reduced" Wigner matrices, in contrast to the full $\mathfrak{D}$ matrices.

In all cases, the result is returned in a 1-dimensional array ordered as

```
[
    dˡₘₚ,ₘ(β)
    for ℓ ∈ 0:ℓₘₐₓ
    for mp ∈ -ℓ:ℓ
    for m ∈ -ℓ:ℓ
]
```

When the first argument is `d`, it will be modified, so it must be at least as large as that array.  When the first argument is `d_storage`, it should be the quantity returned by [`d_prep`](@ref), and the result will be written into the `d` field of that tuple.  Both of these options — especially the latter — reduce the number of allocations needed on each call to the corresponding functions, which should increase the speed significantly.

!!! warn
    When using the `d_storage` argument (which is recommended), the returned quantity `d` will be an alias of `d_storage[1]`.  If you want to retain that data after the next call to [`d_matrices!`](@ref), you should copy it with `copy(d)`.


See also [`d_matrices`](@ref) for a simpler function call when you only need to evaluate the matrices for a single value of `β` or `expiβ`.

# Examples

```julia
using SphericalFunctions
ℓₘₐₓ = 8
T = Float64
β = T(1)/8
d_storage = d_prep(ℓₘₐₓ, T)
d = d_matrices!(d_storage, β)
```
