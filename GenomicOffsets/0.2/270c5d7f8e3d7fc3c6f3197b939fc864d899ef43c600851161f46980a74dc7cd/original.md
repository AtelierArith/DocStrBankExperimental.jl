```
LFMM_Ftest(model::LFMM, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}; genomic_control::Bool=true, center=true) where {T1<:Real,T2<:Real}
```

Compute F-Statistic (F-test) for the Linear Fixed Effects Mixed Model (LFMM). TODO: Add reference & description.

# Arguments

  * `model`: A `LFMM{T<:Real}` data structure (obtained from `RidgeLFMM`).
  * `Y`: A centered genotype matrix of size NxL.
  * `X`: A centered environmental matrix of size NxP.
  * `genomic_control`: If true, apply genomic control to the F-statistic.
  * `center`: If true, both the genotype matrix and the environmental matrix are centered. If false, both matrices are assumed to be centered.

# Returns

  * A vector of p-values for loci in the genotype matrix.
