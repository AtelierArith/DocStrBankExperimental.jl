```
    function BayesLV(v,f,covariates,zeta)
```

  * `v` is the variance for the prior distribution of SNPs.
  * `f` is the model formula for the variance
  * `covariates`is the `DataFrame` that includes explanatory varibles for the variance of each SNP.
  * `zeta` is the error variance in the model for the SNP variances.
  * If `estimateVarZeta` is `true`, it assumes that the error variance for the model for the SNP variances is 0.01 percent of the variance of the log-variances. If `estimateVarZeta` is `false`, it uses `zeta` as the error variance for the log-linear variances (fixed value). If `estimateVarZeta` is a `Float64`, it assumes that the error variance for the model for the SNP variances is `estimateVarZeta` percent of the variance of the log-variances.
