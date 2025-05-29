```
ScalingFit
```

Scaling fit data for an experimental design for a circuit with vertical and horizontal distance parameters, conventionally under depolarising noise.

All fit parameters describe a quadratic as $p[1] + p[2] * dist + p[3] * dist^2$.

# Fields

  * `N::Vector{Int}`: Gate eigenvalues quadratic fit parameters.
  * `N_model::Function`: Quadratic model for the gate eigenvalues.
  * `N_marginal::Vector{Int}`: Marginal gate eigenvalues quadratic fit parameters.
  * `N_marginal_model::Function`: Quadratic model for the marginal gate eigenvalues.
  * `N_relative::Vector{Int}`: Relative gate eigenvalues quadratic fit parameters.
  * `N_relative_model::Function`: Quadratic model for the relative gate eigenvalues.
  * `G::Vector{Int}`: Gate number quadratic fit parameters.
  * `G_model::Function`: Quadratic model for the gate number.
  * `gls_tr::Vector{Float64}`: Ordinary GLS trace quadratic fit parameters.
  * `gls_tr_model::Function`: Quadratic model for the ordinary GLS trace.
  * `gls_tr_sq::Vector{Float64}`: Ordinary GLS trace squared quadratic fit parameters.
  * `gls_tr_sq_model::Function`: Quadratic model for the ordinary GLS trace squared.
  * `gls_expectation_model::Function`: Model for the ordinary GLS expectation.
  * `gls_variance_model::Function`: Model for the ordinary GLS variance.
  * `gls_marginal_tr::Vector{Float64}`: Marginal GLS trace quadratic fit parameters.
  * `gls_marginal_tr_model::Function`: Quadratic model for the marginal GLS trace.
  * `gls_marginal_tr_sq::Vector{Float64}`: Marginal GLS trace squared quadratic fit parameters.
  * `gls_marginal_tr_sq_model::Function`: Quadratic model for the marginal GLS trace squared.
  * `gls_marginal_expectation_model::Function`: Model for the marginal GLS expectation.
  * `gls_marginal_variance_model::Function`: Model for the marginal GLS variance.
  * `gls_relative_tr::Vector{Float64}`: Relative GLS trace quadratic fit parameters.
  * `gls_relative_tr_model::Function`: Quadratic model for the relative GLS trace.
  * `gls_relative_tr_sq::Vector{Float64}`: Relative GLS trace squared quadratic fit parameters.
  * `gls_relative_tr_sq_model::Function`: Quadratic model for the relative GLS trace squared.
  * `gls_relative_expectation_model::Function`: Model for the relative GLS expectation.
  * `gls_relative_variance_model::Function`: Model for the relative GLS variance.
  * `wls_tr::Vector{Float64}`: Ordinary WLS trace quadratic fit parameters.
  * `wls_tr_model::Function`: Quadratic model for the ordinary WLS trace.
  * `wls_tr_sq::Vector{Float64}`: Ordinary WLS trace squared quadratic fit parameters.
  * `wls_tr_sq_model::Function`: Quadratic model for the ordinary WLS trace squared.
  * `wls_expectation_model::Function`: Model for the ordinary WLS expectation.
  * `wls_variance_model::Function`: Model for the ordinary WLS variance.
  * `wls_marginal_tr::Vector{Float64}`: Marginal WLS trace quadratic fit parameters.
  * `wls_marginal_tr_model::Function`: Quadratic model for the marginal WLS trace.
  * `wls_marginal_tr_sq::Vector{Float64}`: Marginal WLS trace squared quadratic fit parameters.
  * `wls_marginal_tr_sq_model::Function`: Quadratic model for the marginal WLS trace squared.
  * `wls_marginal_expectation_model::Function`: Model for the marginal WLS expectation.
  * `wls_marginal_variance_model::Function`: Model for the marginal WLS variance.
  * `wls_relative_tr::Vector{Float64}`: Relative WLS trace quadratic fit parameters.
  * `wls_relative_tr_model::Function`: Quadratic model for the relative WLS trace.
  * `wls_relative_tr_sq::Vector{Float64}`: Relative WLS trace squared quadratic fit parameters.
  * `wls_relative_tr_sq_model::Function`: Quadratic model for the relative WLS trace squared.
  * `wls_relative_expectation_model::Function`: Model for the relative WLS expectation.
  * `wls_relative_variance_model::Function`: Model for the relative WLS variance.
  * `ols_tr::Vector{Float64}`: Ordinary OLS trace quadratic fit parameters.
  * `ols_tr_model::Function`: Quadratic model for the ordinary OLS trace.
  * `ols_tr_sq::Vector{Float64}`: Ordinary OLS trace squared quadratic fit parameters.
  * `ols_tr_sq_model::Function`: Quadratic model for the ordinary OLS trace squared.
  * `ols_expectation_model::Function`: Model for the ordinary OLS expectation.
  * `ols_variance_model::Function`: Model for the ordinary OLS variance.
  * `ols_marginal_tr::Vector{Float64}`: Marginal OLS trace quadratic fit parameters.
  * `ols_marginal_tr_model::Function`: Quadratic model for the marginal OLS trace.
  * `ols_marginal_tr_sq::Vector{Float64}`: Marginal OLS trace squared quadratic fit parameters.
  * `ols_marginal_tr_sq_model::Function`: Quadratic model for the marginal OLS trace squared.
  * `ols_marginal_expectation_model::Function`: Model for the marginal OLS expectation.
  * `ols_marginal_variance_model::Function`: Model for the marginal OLS variance.
  * `ols_relative_tr::Vector{Float64}`: Relative OLS trace quadratic fit parameters.
  * `ols_relative_tr_model::Function`: Quadratic model for the relative OLS trace.
  * `ols_relative_tr_sq::Vector{Float64}`: Relative OLS trace squared quadratic fit parameters.
  * `ols_relative_tr_sq_model::Function`: Quadratic model for the relative OLS trace squared.
  * `ols_relative_expectation_model::Function`: Model for the relative OLS expectation.
  * `ols_relative_variance_model::Function`: Model for the relative OLS variance.
