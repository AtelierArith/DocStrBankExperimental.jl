loco_scan(y::Matrix{Float64}, dfG::DataFrame; kwargs...)

Single trait scan without covariates for LOCO data structure.

# Arguments

  * `y`is the phenotype column matrix.
  * `dfG`is is a dataframe containing genotype values and genotype info such as the chromosome, loci...
  * `kwargs` are optional keywords arguments pertaining to the `BulkLMM.scan()` function. For

```
example: `reml` = false, `permutation_test` = true, `nperms` = 1000, 
`weights` = missing, `prior_variance` = 0.0, `prior_sample_size` = 0.0. Refer to 
`BulkLMM` documentation for more details.
```

# Example

```julia
loco_scan(y, df_geno;
		 reml = false, permutation_test = true, nperms = 1000, 
		 weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

___

loco_scan(y::Matrix{Float64}, G::Vector{Matrix{Float64}}, K::Vector{Matrix{Float64}}; 	kwargs...)

Single trait scan without covariates for LOCO data structure.

# Arguments

  * `y`is the phenotype column matrix.
  * `G`is vector of genotype matrices based on the chromosome.
  * `K` is a vector of kinship matrices.
  * `kwargs` are optional keywords arguments pertaining to the `BulkLMM.scan()` function. For

```
example: `reml` = false, `permutation_test` = true, `nperms` = 1000, 
`weights` = missing, `prior_variance` = 0.0, `prior_sample_size` = 0.0. Refer to 
`BulkLMM` documentation for more details.
```

```julia
loco_scan(y, arr_geno, arr_kinship;
		 reml = false, permutation_test = true, nperms = 1000, 
		 weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

___

loco_scan(y::Matrix{Float64}, G::Vector{Matrix{Float64}}, covar::Matrix{Float64},         K::Vector{Matrix{Float64}};	kwargs...)

Single trait scan with covariates for LOCO data structure.

# Arguments

  * `y`is the phenotype column matrix.
  * `G`is vector of genotype matrices based on the chromosome.
  * `covar` is covariate column matrix.
  * `K` is a vector of kinship matrices.
  * `kwargs` are optional keywords arguments pertaining to the `BulkLMM.scan()` function. For

```
example: `reml` = false, `permutation_test` = true, `nperms` = 1000, 
`weights` = missing, `prior_variance` = 0.0, `prior_sample_size` = 0.0. Refer to 
`BulkLMM` documentation for more details.
```

# Example

```julia
loco_scan(y, arr_geno, covar, arr_kinship;
		 reml = false, permutation_test = true, nperms = 1000, 
		 weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```
