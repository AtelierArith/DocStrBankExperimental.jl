```
fit_transform(f, X, y)
```

Fit and transform the signals `X` with labels `y` based on the LDB class `f`. This function essentially combines both `fit!` and `transform` into one, and is the preferred method when trying to extract the LDB coefficients of the training dataset. For the test dataset, one needs to first run `fit!` on the training dataset before running `transform` on the test dataset. 

# Arguments

  * `f::LocalDiscriminantBasis`: Local discriminant basis object.
  * `Xw::AbstractArray{S} where S<:AbstractFloat`: Group of decomposed signals of the same size, arranged in the 3rd (1D signals) or 4th (2D signals) dimension.
  * `y::AbstractVector{T} where T`: Labels corresponding to each signal in X.

# Returns

  * `Xc::Matrix{S}`: A matrix of the extracted LDB features from `X`, where each column corresponds to the coefficients extracted from the corresponding signal.

# Examples

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
Xc = fit_transform(f, X, y)
```

**See also:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`transform`](@ref),     [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
