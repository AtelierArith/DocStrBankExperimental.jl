```
bootstrap_with_candidates(::Type{GradientForestGO}, rng::Random.AbstractRNG,Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}, Xpred::AbstractMatrix{T2}, nboot::Int=500; ntrees::Int=100, candidates_threshold::Real=0.05, genomic_control::Bool=true, tw_threshold::Real=0.001) where {T1<:Real,T2<:Real}
```

Compute the Gradient Forest genomic offset using a bootstrap approach. For every, bootstrap iteration, the model is fitted using a random subset of the columns of `Y`. The Tracy-Widom test is used to estimate the number of latent factors. The F-test is used to select putatively adaptative loci. The genomic offset is computed for the selected loci.

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator. If not provided, the global RNG is used.
  * `Y::AbstractMatrix{T1}`: NxL matrix with individuals genotypes or allele frequencies.
  * `X::AbstractMatrix{T2}`: NxP matrix with environmental data.
  * `Xpred::AbstractMatrix{T2}`: NxP matrix with the predicted / altered environmental matrix.
  * `nboot::Int=500`: Number of bootstrap iterations.
  * Optional arguments:

      * `ntrees::Int=100`: Number of trees each forest (one per allele) will have.
      * `candidates_threshold::Real=0.05`: Threshold for the F-test. Better to be permisive.
      * `genomic_control::Bool=true`: Apply genomic control to the F-test.
      * `tw_threshold::Real=0.001`: Threshold for the Tracy-Widom test. Better to be conservative (as the number of latent factors is often overconservative).
      * λ::Real=1e-5: Regularization parameter for the LFMM.

# Returns

  * A matrix of size NxNboot with the genomic offset values. If no candidate loci are found, the row is filled with zeros.
