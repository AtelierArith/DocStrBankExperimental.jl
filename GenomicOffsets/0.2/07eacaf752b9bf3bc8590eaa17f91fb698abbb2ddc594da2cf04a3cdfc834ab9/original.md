```
fit(::Type{GeometricGO}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}) where {T1<:Real,T2<:Real}
```

Fit the Geometric genomic offset model (that is, fit a LFMM) using the data `Y` and `X`.

# Arguments

  * `Y::AbstractMatrix{T1}`: NxL matrix with individuals genotypes or allele frequencies.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data.
  * `K`: Number of latent factors to use when fitting th  e LFMM model. It can be determined using the elbow rule of thumb. If nothing is provided, the Tracy-Widom statistic to determine the number of latent factors (which might be overconservative).
  * Optional arguments:

      * `center::Bool=true`: Center both the genotype and environmental data. Predicted environmental data is centered using the same mean as X. If false, data is assumed to be centered.
      * `scale::Bool=true`: Scale the environmental data. Predicted environmental data is scaled using the same standard deviation as X. If false, data is assumed to be scaled.
      * tw_threshold::Real=1e-3: Threshold to determine the number of latent factors if using the Tracy-Widom statistic. By default, it uses 1e-3.
      * λ::Real=1e-5: Regularization parameter for the LFMM.

# Returns

  * A GeometricGO model.
