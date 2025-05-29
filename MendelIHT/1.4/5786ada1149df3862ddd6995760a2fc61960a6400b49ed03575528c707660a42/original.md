```
cross_validate(filename, d, path=1:20, phenotypes=6, covariates="", 
    cv_summaryfile="cviht.summary.txt", q=5, kwargs...)
```

Runs cross-validation to determinal optimal sparsity level `k`. Different sparsity levels are specified in `path`. 

# Arguments

  * `filename`: A `String` for VCF, binary PLINK, or BGEN file. VCF files should end   in `.vcf` or `.vcf.gz`. Binary PLINK files should exclude `.bim/.bed/.fam`   trailings but the trio must all be present in the same directory. BGEN files   should end in `.bgen`.
  * `d`: Distribution of phenotypes. Specify `Normal` for quantitative traits,   `Bernoulli` for binary traits, `Poisson` or `NegativeBinomial` for   count traits, and `MvNormal` for multiple quantitative traits.

# Optional Arguments

  * `path`: Different values of `k` that should be tested. One can input a vector of    `Int` (e.g. `path=[5, 10, 15, 20]`) or a range (default `path=1:20`).
  * `phenotypes`: Phenotype file name (`String`), an integer, or vector of integer. Integer(s)   coresponds to the column(s) of `.fam` file that stores phenotypes (default 6).    We recognize missing phenotypes as `NA` or `-9`. For quantitative traits   (univariate or multivariate), missing phenotypes are imputed with the mean. Binary   and count phenotypes cannot be imputed. Phenotype files are read using `readdlm` function   in Julia base. We require each subject's phenotype to occupy a different row, and for    multivariate analysis, each phenotype is comma separated. The phenotype file   should not include a header line. Each row should be listed in the same order as in   the PLINK.
  * `covariates`: Covariate file name. Default `covariates=""` (in which case an intercept   term will be automatically included). If `covariates` file specified, it will be    read using `readdlm` function in Julia base. We require the covariate file to be   comma separated, and not include a header line. Each row should be listed in the   same order as in the PLINK. The first column should be all 1s to indicate an   intercept. All other columns not specified in `exclude_std_idx` will be standardized   to mean 0 variance 1
  * `cv_summaryfile`: Output file name for saving IHT's cross validation summary statistics.   Default `cv_summaryfile="cviht.summary.txt"`.
  * `q`: Number of cross validation folds. Larger means more accurate and more computationally   intensive. Should be larger 2 and smaller than 10. Default `q=5`.
  * `dosage`: Currently only guaranteed to work for VCF files. If `true`, will read   genotypes dosages (i.e. `X[i, j] ∈ [0, 2]` before standardizing)
  * All optional arguments available in [`cv_iht`](@ref)

# Output

A vector `mse` of cross-validated mean-squared errors (technically deviance residuals), where `mse[i]` is the error of sparsity level `path[i]`. In addition, a human-readable text file is also outputted with file name specified with `cv_summaryfile`.
