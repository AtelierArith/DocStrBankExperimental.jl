```
variational_expectation!(model::SwitchingLinearDynamicalSystem, y, FB, FS) -> Float64
```

Compute the variational expectation (Evidence Lower Bound, ELBO) for a Switching Linear Dynamical System.

# Arguments

  * `model::SwitchingLinearDynamicalSystem`:   The switching linear dynamical system model containing parameters such as the number of regimes (`K`), system matrices (`B`), and observation models.
  * `y`:   The observation data, typically a matrix where each column represents an observation at a specific time step.
  * `FB`:   The forward-backward object that holds variables related to the forward and backward passes, including responsibilities (`γ`).
  * `FS`:   An array of `FilterSmooth` objects, one for each regime, storing smoothed state estimates and covariances.

# Returns

  * `Float64`:   The total Evidence Lower Bound (ELBO) computed over all regimes and observations.

# Description

This function performs the variational expectation step for a Switching Linear Dynamical System by executing the following operations:

1. **Extract Responsibilities**:   Retrieves the responsibilities (`γ`) from the forward-backward object and computes their exponentials (`hs`).
2. **Parallel Smoothing and Sufficient Statistics Calculation**:   For each regime `k` from `1` to `model.K`, the function:

      * Performs smoothing using the `smooth` function to obtain smoothed states (`x_smooth`), covariances (`p_smooth`), inverse off-diagonal terms, and total entropy.
      * Computes sufficient statistics (`E_z`, `E_zz`, `E_zz_prev`) from the smoothed estimates.
      * Calculates the ELBO contribution for the current regime and accumulates it into `ml_total`.
3. **Update Variational Distributions**:  

      * Computes the variational distributions (`qs`) from the smoothed states, which are stored as log-likelihoods in `FB`.
      * Executes the forward and backward passes to update the responsibilities (`γ`) based on the new `qs`.
      * Recalculates the responsibilities (`γ`) to reflect the updated variational distributions.
4. **Return ELBO**:   Returns the accumulated ELBO (`ml_total`), which quantifies the quality of the variational approximation.

# Example

```julia

# Assume `model` is an instance of SwitchingLinearDynamicalSystem with K regimes

# `y` is the observation matrix of size (num*features, num*time_steps)

# `FB` is a pre-initialized ForwardBackward object

# `FS` is an array of FilterSmooth objects, one for each regime

elbo = variational_expectation!(model, y, FB, FS) println("Computed ELBO: ", elbo)
