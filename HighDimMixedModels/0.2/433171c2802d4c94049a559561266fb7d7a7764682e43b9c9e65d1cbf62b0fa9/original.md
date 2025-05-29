```
HDMModel
```

Results of a fitted model

# Fields

  * `data`: NamedTuple containing the input data used for fitting the model
  * `weights`: Vector of penalty weights used in the model
  * `init_coef`: NamedTuple containing the initial coefficient values
  * `init_log_like`: Initial log-likelihood value
  * `init_objective`: Initial objective function value
  * `init_nz`: Number of non-zero components in the initial estimate of fixed effects
  * `penalty`: String indicating the type of penalty used in the model
  * `standardize`: Boolean indicating whether the input data was standardized
  * `λ`: Regularization hyperparameter
  * `scada`: Hyperparameter relevant to the scad penalty
  * `σ²`: Estimated variance parameter
  * `L`: Lower triangular matrix representing the Cholesky factor of the random effect covariance matrix
  * `fixef`: Vector of estimated fixed effects
  * `ranef`:  vector of g vectors, each of length m, holding random effects BLUPs for each group
  * `fitted`: Vector of fitted values, including random effects
  * `resid`: Vector of residuals, including random effects
  * `log_like`: Log-likelihood value at convergence
  * `objective`: Objective function value at convergence
  * `npar`: Total number of parameters in the model
  * `nz`: Number of non-zero fixed effects
  * `deviance`: Deviance value
  * `num_arm`: Number of times `armijo!` needed to be called
  * `arm_con`: Number of times the Armijo algorithm failed to converge
  * `aic`: Akaike Information Criterion
  * `bic`: Bayesian Information Criterion
  * `iterations`: Number of iterations performed
  * `ψstr`: Assumed structure of the random effect covariance matrix
  * `ψ`: Estimated random effect covariance matrix, i.e. L * L'
  * `control`: Control object containing hyperparameters that were used for the coordinate descent algorithm
