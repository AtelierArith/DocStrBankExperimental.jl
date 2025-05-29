```
discriminant_power(D, tree, dp)
discriminant_power(coefs, y, dp)
```

Returns the discriminant power of each leaf from the local discriminant basis (LDB) tree. 

# Arguments

  * `D::AbstractArray{T} where T<:AbstractFloat`: Discriminant measures.
  * `tree::BitVector`: Best basis tree for selecting coefficients with largest discriminant measures.
  * `coefs::AbstractArray{T} where T<:AbstractFloat`: Best basis coefficients for the input signals.
  * `y::AbstractVector{S} where S`: Labels corresponding to each signal in `coefs`.
  * `dp::DiscriminantPower`: The measure for discriminant power.

!!! note
    `discriminant_power(D, tree, dp)` only works for `dp = BasisDiscriminantMeasure()`, whereas `discriminant_power(coefs, y, dp)` works for `dp = FishersClassSeparability()` and `dp = RobustFishersClassSeparability()`.


# Returns

  * `power::Array{T}`: The discriminant power at each index of `D` or `coefs`.
  * `order::Vector{T}`: The order of discriminant power in descending order.
