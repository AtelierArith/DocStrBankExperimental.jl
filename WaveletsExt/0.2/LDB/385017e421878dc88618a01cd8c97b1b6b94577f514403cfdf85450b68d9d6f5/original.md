```
inverse_transform(f, X)
```

Compute the inverse transform on the feature matrix `X` to form the original signal based on the LDB class `f`. This function can be used to reconstruct the signals and compare the reconstructed features between different classes.

# Arguments

  * `f::LocalDiscriminantBasis`: Local discriminant basis object.
  * `X::Matrix{S} where S<:AbstractFloat`: A matrix of the extracted LDB features from original signals, where each column corresponds to the coefficients extracted from the corresponding signal.

# Returns

  * `Xₜ::Array{S}`: Reconstructed signals.

# Examples

```julia
X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
Xc = fit_transform(f, X, y)
Xₜ = inverse_transform(f, Xc)
```

**See also:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`change_nfeatures`](@ref)
