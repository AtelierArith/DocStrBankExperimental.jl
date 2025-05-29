```
    function SNP(name,path;map="")
```

  * Defines SNP information for further analysis.
  * `path` is the path for the marker file, or the matrix for the marker genotypes.
  * Marker files are currently expected to be ordered as the phenotype data.
  * The method to be applied to the data, `GBLUP`, `BayesB`, `BayesR` etc, is defined in the prior setting.
  * Map file is optional. If not provided, a Bayesian Regression model with common variance for all SNPs will be applied. If provided, shoul match the order in the genotype file.
  * One most avoid overlapping marker sets by using different `name`s.
