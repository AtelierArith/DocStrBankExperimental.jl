```
 kinship_std(genmat::Array{Float64,2})
```

Calculates a kinship by a standardized (or normalized) genotype matrix (linear kernel), i.e. genotypes subtracted by marker mean and divided by marker standard deviation. It can also do with climatic information data. See [`kinship_gs`](@ref).

# Argument

  * `genmat` : A matrix of genotype data (0,1,2). size(genmat)=(n,p) for `n` individuals x `p` markers

# Output

Returns a n x n symmetric matrix. See also [`kinship_ctr`](@ref).
