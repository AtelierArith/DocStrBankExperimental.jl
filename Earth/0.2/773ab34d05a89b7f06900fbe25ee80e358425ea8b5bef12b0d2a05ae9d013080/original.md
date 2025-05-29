```
fit(EarthModel, X, y; config::EarthConfig=EarthConfig(), prune=true, verbosity=0)
```

Fit a regression model using an approach similar to Friedman's 1991 MARS procedure (also known as Earth for trademark reasons).  The covariates are in `X` and the vector `y` contains the response values.

Earth/MARS involves two steps: a greedy basis construction followed by pruning step that aims to eliminate irrelevant terms.  The basis functions are products of hinge functions.  This implementation uses the Lasso instead of back-selection to prune the model.

The covariates `X` can be a numeric Matrix, a data frame, a vector or tuple of vectors, or a named tuple whose values are vectors.  In the latter two cases, each covariate vector must be of numeric or string type, or an instance of CategoricalArray. The latter-two types are expanded into binary indicator vectors.

The `config` argument can be used to specify many aspects of how the model is fit.  See `EarthConfig` for more specifics.

References:

Friedman (1991) "Multivariate Adaptive Regression Splines". Ann. Statist. 19(1): 1-67 (March, 1991). DOI: 10.1214/aos/1176347963 https://projecteuclid.org/journals/annals-of-statistics/volume-19/issue-1/Multivariate-Adaptive-Regression-Splines/10.1214/aos/1176347963.full

# Keyword arguments

  * `weights`: optional case weights
  * `config`: permits configuration of many tuning parameters
  * `verbosity`: Print some information as the fitting algorithm runs
