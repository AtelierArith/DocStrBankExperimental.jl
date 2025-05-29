```
fitdec!(f, Xw, y)
```

Fits the Local Discriminant Basis feature selection algorithm `f` onto the decomposed signals `Xw` with labels `y`.

# Arguments

  * `f::LocalDiscriminantBasis`: Local discriminant basis object.
  * `Xw::AbstractArray{S} where S<:AbstractFloat`: Group of decomposed signals of the same size, arranged in the 3rd (1D signals) or 4th (2D signals) dimension.
  * `y::AbstractVector{T} where T`: Labels corresponding to each signal in X.

# Returns

  * `f::LocalDiscriminantBasis`: The same LDB object `f` with updated fields.

# Examples

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
Xw = wpdall(X, f.wt)
fitdec!(f, Xw, y)
```

**See also:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
