```
fit(::Type{RONA}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}) where {T1<:Real,T2<:Real}
```

Fit the RONA model (that is, solve the least squares problem) using the data `Y` and `X`.

# Arguments

  * `Y::AbstractMatrix{T1}`: NxL matrix with individuals genotypes or allele frequencies.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data.

# Returns

  * A RONA model.
