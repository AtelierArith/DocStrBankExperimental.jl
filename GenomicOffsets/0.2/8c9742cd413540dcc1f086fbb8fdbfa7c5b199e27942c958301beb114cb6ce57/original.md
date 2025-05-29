```
fit(::Type{RDAGO}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}) where {T1<:Real,T2<:Real}
```

Fit the RDA model (that is, apply Redundancy Analysis) using the data `Y` and `X`.

# Arguments

  * `Y::AbstractMatrix{T1}`: NxL matrix with individuals genotypes or allele frequencies.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data.
  * Optional arguments:

      * `K::Int=size(Y,2)`: Number of main canonical axes to retain. The final number of axes is determined either by K or pratio.
      * `pratio::Float64=0.99`: The ratio of variances preserved in the principal subspace.

# Returns

  * A RDAGO model.
