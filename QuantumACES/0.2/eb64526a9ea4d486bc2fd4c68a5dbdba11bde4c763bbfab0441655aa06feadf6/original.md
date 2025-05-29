```
EnsembleFit
```

Ensemble scaling fit data for an experimental design for a circuit with vertical and horizontal distance parameters under a random noise model.

All pair fit parameters correspond to the trace and trace squared quadratic terms appearing in the expressions for the expectation and variance.

# Fields

  * `gls_pair::Vector{Float64}`: Ordinary GLS pair quadratic fit parameters.
  * `gls_expectation_model::Function`: Model for the ordinary GLS expectation.
  * `gls_variance_model::Function`: Model for the ordinary GLS variance.
  * `gls_marginal_pair::Vector{Float64}`: Marginal GLS pair quadratic fit parameters.
  * `gls_marginal_expectation_model::Function`: Model for the marginal GLS expectation.
  * `gls_marginal_variance_model::Function`: Model for the marginal GLS variance.
  * `gls_relative_pair::Vector{Float64}`: Relative GLS pair quadratic fit parameters.
  * `gls_relative_expectation_model::Function`: Model for the relative GLS expectation.
  * `gls_relative_variance_model::Function`: Model for the relative GLS variance.
  * `wls_pair::Vector{Float64}`: Ordinary WLS pair quadratic fit parameters.
  * `wls_expectation_model::Function`: Model for the ordinary WLS expectation.
  * `wls_variance_model::Function`: Model for the ordinary WLS variance.
  * `wls_marginal_pair::Vector{Float64}`: Marginal WLS pair quadratic fit parameters.
  * `wls_marginal_expectation_model::Function`: Model for the marginal WLS expectation.
  * `wls_marginal_variance_model::Function`: Model for the marginal WLS variance.
  * `wls_relative_pair::Vector{Float64}`: Relative WLS pair quadratic fit parameters.
  * `wls_relative_expectation_model::Function`: Model for the relative WLS expectation.
  * `wls_relative_variance_model::Function`: Model for the relative WLS variance.
  * `ols_pair::Vector{Float64}`: Ordinary OLS pair quadratic fit parameters.
  * `ols_expectation_model::Function`: Model for the ordinary OLS expectation.
  * `ols_variance_model::Function`: Model for the ordinary OLS variance.
  * `ols_marginal_pair::Vector{Float64}`: Marginal OLS pair quadratic fit parameters.
  * `ols_marginal_expectation_model::Function`: Model for the marginal OLS expectation.
  * `ols_marginal_variance_model::Function`: Model for the marginal OLS variance.
  * `ols_relative_pair::Vector{Float64}`: Relative OLS pair quadratic fit parameters.
  * `ols_relative_expectation_model::Function`: Model for the relative OLS expectation.
  * `ols_relative_variance_model::Function`: Model for the relative OLS variance.
