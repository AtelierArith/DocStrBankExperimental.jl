```julia
struct MRing{T, V<:Union{AbstractArray{T, 1}, NTuple{N, T} where {N, T}}} <: VLBISkyModels.GeometricModel{T}
```

m-ring geometric model. This is a infinitely thin unit flux delta ring whose angular structure is given by a Fourier expansion. That is,

```
I(r,θ) = (2π)⁻¹δ(r-1)∑ₙ(αₙcos(nθ) - βₙsin(nθ))
```

The `N` in the type defines the order of the Fourier expansion.

# Fields

  * `α`: Real Fourier mode coefficients

  * `β`: Imaginary Fourier mode coefficients
