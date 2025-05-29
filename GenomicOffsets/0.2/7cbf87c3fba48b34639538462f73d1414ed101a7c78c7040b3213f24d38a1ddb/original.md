```
fit(::Type{GradientForestGO}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}; ntrees::Int=100) where {T1<:Real,T2<:Real}
```

Fit the Gradient forest genomic offset model (that is, fit a Gradient Forest) using the data `Y` and `X`.

# Arguments

  * `Y::AbstractMatrix{T1}`: NxL matrix with individuals genotypes or allele frequencies.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data.
  * `ntrees`: Number of trees each forest (one per allele) will have.

# Returns

  * A GradientForestGO model.
