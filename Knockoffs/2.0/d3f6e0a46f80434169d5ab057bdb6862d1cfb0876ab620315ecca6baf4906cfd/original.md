```
hmm_knockoff(snpdata::SnpData, r::AbstractVecOrMat, θ::AbstractMatrix, α::AbstractMatrix)
```

Generates knockoff of `snpdata` with loaded r, θ, α

# Input

  * `SnpData`: A `SnpData` object from SnpArrays
  * `r`: The r vector estimated by fastPHASE
  * `θ`: The θ matrix estimated by fastPHASE
  * `α`: The α matrix estimated by fastPHASE

# Optional Inputs

  * `outdir`: Output directory for generated knockoffs
  * `plink_outfile`: Output file name for knockoff genotypes
  * `estimate_δ`: If true, will estimate pseudo-FDR by computing a δ value    for each SNP via likelihood ratio bound
