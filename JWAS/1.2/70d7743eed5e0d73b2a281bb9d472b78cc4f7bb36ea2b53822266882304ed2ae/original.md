```
GWAS(marker_effects_file,model;header=true,window_size=100,threshold=0.001)
```

run genomic window-based GWAS without a map file

  * MCMC samples of marker effects are stored in **marker*effects*file** with delimiter ','.
  * **window_size** is either a constant (identical number of markers in each window) or an array of number of markers in each window
  * **model** is either the model::MME used in analysis or the genotypic covariate matrix M::Array
  * File format:
