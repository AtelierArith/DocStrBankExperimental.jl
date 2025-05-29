```
 kinship_ctr(genmat::Array{Float64,2})
```

Calculates a kinship by a centered genotype matrix (linear kernel), i.e. genotypes subtracted by marker mean.

# Argument

  * `genmat` : A matrix of genotype data (0,1,2). size(genmat)=(n,p) for `n` individuals x `p` markers

# Output

Returns a n x n symmetric matrix. See also [`kinship_std`](@ref).
