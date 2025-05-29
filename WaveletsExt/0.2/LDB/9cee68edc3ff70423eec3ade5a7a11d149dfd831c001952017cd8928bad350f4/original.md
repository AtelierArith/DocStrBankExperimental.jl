```
change_nfeatures(f, x, n_features)
```

Change the number of features extracted from the signals from `f.n_features` to `n_features`. 

!!! warning If the input `n_features` is larger than `f.n_features`, it results in the     regeneration of signals based on the current `f.n_features` before reselecting the     features. This will cause additional features to be less accurate and effective. Often     times, the "additional" features tend to be zeros.

# Arguments

  * `f::LocalDiscriminantBasis`: Local discriminant basis object.
  * `x::AbstractMatrix{S} where S<:AbstractFloat`: A matrix of the extracted LDB features from original signals, where each column corresponds to the coefficients extracted from the corresponding signal.
  * `n_features::Integer`: Desired number of features in selected by LDB.

# Returns

  * `xₜ::Matrix{S}`: Matrix of extracted LDB features, where the number of rows is now `n_features` instead of the previous `f.n_features`.

**See also:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`inverse_transform`](@ref)
