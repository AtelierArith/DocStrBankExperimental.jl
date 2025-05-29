A Mondrian random forest is determined by:

  * `lambda`: the non-negative lifetime parameter
  * `n_trees`: the number of Mondrian trees in the forest
  * `n_data`: the number of data points
  * `n_evals`: the number of evaluation points
  * `x_evals`: the evaluation points
  * `significance_level`: the significance level for confidence intervals
  * `X_data`: the covariate data
  * `Y_data`: the response data
  * `trees`: a list of the trees used in the forest
  * `mu_hat`: the estimated regression function
  * `sigma2_hat`: the estimated residual variance function
  * `Sigma_hat`: the estimated forest variance function
  * `confidence_band`: a confidence band for the regression function
