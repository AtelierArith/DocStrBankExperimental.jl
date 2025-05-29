```
fit_vi(model; n_samples=4000, n_iterations=10, n_elbo_samples=20, 
       optimizer=AutoForwardDiff())
```

Perform variational inference using ADVI (Automatic Differentiation Variational Inference).

# Arguments

  * `model`: Model instance to perform inference on
  * `n_samples::Int=4000`: Number of posterior samples to draw
  * `n_iterations::Int=10`: Number of ADVI iterations
  * `n_elbo_samples::Int=20`: Number of samples for ELBO estimation
  * `optimizer=AutoForwardDiff()`: Optimization algorithm for ADVI

# Returns

  * `ADVIResults`: Container with inference results including:

      * Posterior samples
      * MAP estimates
      * Parameter variances
      * Full Turing chain

# Notes

Uses Turing.jl's ADVI implementation for fast approximate Bayesian inference. The model is automatically constructed with appropriate priors and likelihood.
