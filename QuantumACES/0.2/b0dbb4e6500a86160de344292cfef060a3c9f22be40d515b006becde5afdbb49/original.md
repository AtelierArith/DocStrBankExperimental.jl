```
Merit
```

Merit parameters for an experimental design.

# Fields

  * `circuit_param::AbstractCircuitParameters`: Circuit parameters.
  * `noise_param::AbstractNoiseParameters`: Noise parameters.
  * `tuple_set_data::TupleSetData`: [`TupleSetData`](@ref) object that generates the tuple set.
  * `tuple_times::Vector{Float64}`: Time taken to implement the circuit corresponding to each tuple, normalised according to the basic tuple set.
  * `shot_weights::Vector{Float64}`: Shot weights for each tuple in the set, which add to 1.
  * `experiment_numbers::Vector{Int}`: Number of experiments for each tuple in the set.
  * `experiment_number::Int`: Total number of experiments.
  * `N::Int`: Number of gate eigenvalues.
  * `N_marginal::Int`: Number of marginal gate eigenvalues.
  * `N_relative::Int`: Number of relative precision marginal gate eigenvalues.
  * `G::Int`: Total number of gates.
  * `gls_expectation::Float64`: Expected normalised RMS error for the generalised least squares (GLS) gate eigenvalue estimator vector.
  * `gls_variance::Float64`: Normalised RMS error variance for the GLS gate eigenvalue estimator vector.
  * `gls_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the GLS gate eigenvalue estimator covariance matrix.
  * `gls_marginal_expectation::Float64`: Expected normalised RMS error for the marginal GLS gate eigenvalue estimator vector.
  * `gls_marginal_variance::Float64`: Normalised RMS error variance for the marginal GLS gate eigenvalue estimator vector.
  * `gls_marginal_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the marginal GLS gate eigenvalue estimator covariance matrix.
  * `gls_relative_expectation::Float64`: Expected normalised RMS error for the relative precision marginal GLS gate eigenvalue estimator vector.
  * `gls_relative_variance::Float64`: Normalised RMS error variance for the relative precision marginal GLS gate eigenvalue estimator vector.
  * `gls_relative_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the relative precision marginal GLS gate eigenvalue estimator covariance matrix.
  * `wls_expectation::Float64`: Expected normalised RMS error for the weighted least squares (WLS) gate eigenvalue estimator vector.
  * `wls_variance::Float64`: Normalised RMS error variance for the WLS gate eigenvalue estimator vector.
  * `wls_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the WLS gate eigenvalue estimator covariance matrix.
  * `wls_marginal_expectation::Float64`: Expected normalised RMS error for the marginal WLS gate eigenvalue estimator vector.
  * `wls_marginal_variance::Float64`: Normalised RMS error variance for the marginal WLS gate eigenvalue estimator vector.
  * `wls_marginal_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the marginal WLS gate eigenvalue estimator covariance matrix.
  * `wls_relative_expectation::Float64`: Expected normalised RMS error for the relative precision marginal WLS gate eigenvalue estimator vector.
  * `wls_relative_variance::Float64`: Normalised RMS error variance for the relative precision marginal WLS gate eigenvalue estimator vector.
  * `wls_relative_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the relative precision marginal WLS gate eigenvalue estimator covariance matrix.
  * `ols_expectation::Float64`: Expected normalised RMS error for the ordinary least squares (OLS) gate eigenvalue estimator vector.
  * `ols_variance::Float64`: Normalised RMS error variance for the OLS gate eigenvalue estimator vector.
  * `ols_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the OLS gate eigenvalue estimator covariance matrix.
  * `ols_marginal_expectation::Float64`: Expected normalised RMS error for the marginal OLS gate eigenvalue estimator vector.
  * `ols_marginal_variance::Float64`: Normalised RMS error variance for the marginal OLS gate eigenvalue estimator vector.
  * `ols_marginal_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the marginal OLS gate eigenvalue estimator covariance matrix.
  * `ols_relative_expectation::Float64`: Expected normalised RMS error for the relative precision marginal OLS gate eigenvalue estimator vector.
  * `ols_relative_variance::Float64`: Normalised RMS error variance for the relative precision marginal OLS gate eigenvalue estimator vector.
  * `ols_relative_cov_eigenvalues::Vector{Float64}`: Eigenvalues of the relative precision marginal OLS gate eigenvalue estimator covariance matrix.
  * `cond_num::Float64`: Condition number of the design matrix, the ratio of the largest and smallest singular values.
  * `pinv_norm::Float64`: Pseudoinverse norm of the design matrix, the inverse of the smallest singular value.
