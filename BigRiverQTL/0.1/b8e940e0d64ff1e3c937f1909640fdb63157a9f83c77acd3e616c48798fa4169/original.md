```
 shrinkg(f,nb::Int64,geno)
```

Estimates a full-rank positive definite kinship matrix by shrinkage intensity estimation (bootstrap).  It can only be used with [`kinship_man`](@ref), [`kinship_4way`](@ref). This function runs faster by CPU parallelization.  Add workers/processes using `addprocs()` function before running for speedup.

# Arguments

  * `f`: A function of computing a kinship. It can only be used with [`kinship_man`](@ref), [`kinship_4way`](@ref).
  * `nb` : An integer indicating the number of bootstraps. It does not have to be a large number.
  * `geno` : A matrix of genotypes. See [`kinship_man`](@ref), [`kinship_4way`](@ref) for dimension.

# Example

```julia
julia> using flxQTL
julia> addprocs(8)
julia> K = shinkage(kinshipMan,20,myGeno)
```

# Output

_ Returns a full-rank symmetric positive definite matrix.
