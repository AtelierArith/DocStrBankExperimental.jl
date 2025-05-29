Covariance Matrix Adaptation Evolution Strategy Implementation: (μ/μ_{I,W},λ)-CMA-ES

The constructor takes following keyword arguments:

  * `μ`/`mu` is the number of parents
  * `λ`/`lambda` is the number of offspring
  * `c_1` is a learning rate for the rank-one update of the covariance matrix update
  * `c_c` is a learning rate for cumulation for the rank-one update of the covariance matrix
  * `c_mu` is a learning rate for the rank-$\mu$ update of the covariance matrix update
  * `c_sigma` is a learning rate for the cumulation for the step-size control
  * `c_m` is the learning rate for the mean update, $c_m \leq 1$
  * `σ0`/`sigma0` is the initial step size `σ`
  * `weights` are recombination weights, if the weights are set to $1/\mu$ then the *intermediate* recombination is activated.
  * `metrics` is a collection of convergence metrics.
