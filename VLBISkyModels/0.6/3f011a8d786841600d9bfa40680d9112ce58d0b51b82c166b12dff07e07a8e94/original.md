```julia
struct ExtendedRing{T} <: VLBISkyModels.GeometricModel{T}
```

A symmetric extended ring whose radial profile follows an inverse gamma distributions.

The formula in the image domain is given by

```
I(r,θ) = βᵅrᵅ⁻²exp(-β/r)/2πΓ(α)
```

where `α = shape` and `β = shape+1`

# Note

We mainly use this as an example of a non-analytic Fourier transform (although it has a complicated expression)

# Fields

  * `shape`: shape of the radial distribution

Note that if `T` isn't specified at construction then it defaults to `Float64`.
