```
fit!(f, X, y)
```

Fits the Local Discriminant Basis feature selection algorithm `f` onto the signals `X` with labels `y`.

# Arguments

  * `f::LocalDiscriminantBasis`: Local discriminant basis object.
  * `X::AbstractArray{S} where S<:AbstractFloat`: Group of signals of the same size, arranged in the 2nd (1D signals) or 3rd (2D signals) dimension.
  * `y::AbstractVector{T} where T`: Labels corresponding to each signal in X.

# Returns

  * `f::LocalDiscriminantBasis`: The same LDB object `f` with updated fields.

# Examples

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
fit!(f, X, y)
```

**See also:** [`LocalDiscriminantBasis`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
