```
iht(filename, k, d, phenotypes=6, covariates="", summaryfile="iht.summary.txt",
    betafile="iht.beta.txt", kwargs...)
```

Runs IHT with sparsity level `k`. 

# Arguments

  * `filename`: A `String` for VCF, binary PLINK, or BGEN file. VCF files should end   in `.vcf` or `.vcf.gz`. Binary PLINK files should exclude `.bim/.bed/.fam`   trailings but the trio must all be present in the same directory. BGEN files   should end in `.bgen`.
  * `k`: An `Int` for sparsity parameter = number of none-zero coefficients
  * `d`: Distribution of phenotypes. Specify `Normal` for quantitative traits,   `Bernoulli` for binary traits, `Poisson` or `NegativeBinomial` for   count traits, and `MvNormal` for multiple quantitative traits.

# Optional Arguments

  * `phenotypes`: Phenotype file name (`String`), an integer, or vector of integer. Integer(s)   coresponds to the column(s) of PLINK's `.fam` file that stores phenotypes (default `phenotypes=6`).    Enter multiple integers for multivariate analysis (e.g. `phenotypes=[6, 7]`).   We recognize missing phenotypes as `NA` or `-9`. For quantitative traits   (univariate or multivariate), missing phenotypes are imputed with the mean. Binary   and count phenotypes cannot be imputed. Phenotype files are read using `readdlm` function   in Julia base. We require each subject's phenotype to occupy a different row, and for    multivariate analysis, each phenotype is comma separated. The phenotype file   should not include a header line. Each row should be listed in the same order as in   the PLINK and (for multivariate analysis) be comma separated.
  * `covariates`: Covariate file name. Default `covariates=""` (in which case an intercept   term will be automatically included). If `covariates` file specified, it will be    read using `readdlm` function in Julia base. We require the covariate file to be   comma separated, and not include a header line. Each row should be listed in the   same order as in the PLINK. The first column should be all 1s to indicate an   intercept. All other columns not specified in `exclude_std_idx` will be standardized   to mean 0 variance 1.
  * `summaryfile`: Output file name for saving IHT's summary statistics. Default   `summaryfile="iht.summary.txt"`.
  * `betafile`: Output file name for saving IHT's estimated genotype effect sizes.    Default `betafile="iht.beta.txt"`.
  * `covariancefile`: Output file name for saving IHT's estimated trait covariance   matrix for multivariate analysis. Default `covariancefile="iht.cov.txt"`.
  * `exclude_std_idx`: Indices of non-genetic covariates that should be excluded from   standardization.
  * `dosage`: Currently only guaranteed to work for VCF files. If `true`, will read   genotypes dosages (i.e. `X[i, j] ∈ [0, 2]` before standardizing)
  * All optional arguments available in [`fit_iht`](@ref)

# Output

A fitted `IHTResult` (univariate analysis) or `mIHTResult` (multivariate analysis). In addition, a human-readable text file is also outputted with file name specified with `betafile`.
