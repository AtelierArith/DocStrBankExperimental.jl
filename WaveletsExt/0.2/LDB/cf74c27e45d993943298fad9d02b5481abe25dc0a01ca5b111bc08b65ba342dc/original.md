```
transform(f, X)
```

Extract the LDB features from signals `X` based on the LDB tree constructed from previously fitted signals.

# Arguments

  * `f::LocalDiscriminantBasis`: Local discriminant basis object.
  * `X::AbstractArray{S} where S<:AbstractFloat`: Group of signals of the same size, arranged in the 2nd (1D signals) or 3rd (2D signals) dimension.

# Returns

  * `Xc::Matrix{S}`: A matrix of the extracted LDB features from `X`, where each column corresponds to the coefficients extracted from the corresponding signal.

# Examples

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
fit!(f, X, y)
Xc = transform(f, X)
```

**See also:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
