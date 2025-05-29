```
WeightedValidation(weighting, folding; lambda=1.0, loss=Dict())
```

An error estimation method which samples are weighted with `weighting` method and split into folds with `folding` method. Weights are raised to `lambda` power in `[0,1]`. Optionally, specify a dictionary with `loss` functions from `LossFunctions.jl` for some of the variables.

## References

  * Sugiyama et al. 2006. [Importance-weighted cross-validation for covariate shift](https://link.springer.com/chapter/10.1007/11861898_36)
  * Sugiyama et al. 2007. [Covariate shift adaptation by importance weighted cross validation](http://www.jmlr.org/papers/volume8/sugiyama07a/sugiyama07a.pdf)
