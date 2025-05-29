```
build_laplace_objective(build_latent_gp, xs, ys; kwargs...)
```

Construct a closure that computes the minimisation objective for optimising hyperparameters of the latent GP in the Laplace approximation. The returned closure passes its arguments to `build_latent_gp`, which must return the `LatentGP` prior.

# Keyword arguments

  * `newton_warmstart=true`: (default) begin Newton optimisation at the mode of the previous call to the objective
  * `newton_callback`: called as `newton_callback(fnew, cache)` after each Newton step
  * `newton_maxiter=100`: maximum number of Newton steps.
