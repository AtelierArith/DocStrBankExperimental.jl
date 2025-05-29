```
ghost_knockoffs(Zscores, D, Σinv; [m=1])
```

Generate Ghost knockoffs given a list of z-scores (GWAS summary statistic). 

# Inputs

  * `Zscores`: List of z-score statistics
  * `D`: Matrix obtained from solving the knockoff problem satisfying    `(m+1)/m*Σ - D ⪰ 0`
  * `Σinv`: Inverse of the covariance matrix

# optional inputs

  * `m`: Number of knockoffs

# Reference

He, Z., Liu, L., Belloy, M. E., Le Guen, Y., Sossin, A., Liu, X., ... & Ionita-Laza, I. (2021).  Summary statistics knockoff inference empowers identification of putative causal variants in  genome-wide association studies. 
