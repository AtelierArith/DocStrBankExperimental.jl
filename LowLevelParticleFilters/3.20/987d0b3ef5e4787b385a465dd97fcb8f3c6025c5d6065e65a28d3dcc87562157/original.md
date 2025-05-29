```
IMM(models, P, μ; check = true, p = NullParameters(), interact = true)
```

Interacting Multiple Model (IMM) filter. This filter is a combination of multiple Kalman-type filters, each with its own state and covariance. The IMM filter is a probabilistically weighted average of the states and covariances of the individual filters. The weights are determined by the probability matrix `P` and the mixing probabilities `μ`.

This implmentation allows for any combination of Kalman-type estimators to be used in the internal ensemble of models, and is not limited to linear estimators. This class of models encompasses others, such as 

  * Jump Markov Linear Systems (JMLS)
  * Multiple-model filters (interactivity can be turned off by setting `interact=false`)
  * Multiple Hypothesis Tracking (MHT)

!!! warning "Experimental"
    This filter is currently considered experimental and the user interface may change in the future without respecting semantic versioning.


In addition to the [`predict!`](@ref) and [`correct!`](@ref) steps, the IMM filter has an [`interact!`](@ref) method that updates the states and covariances of the individual filters based on the mixing probabilities. The [`combine!`](@ref) method combines the states and covariances of the individual filters into a single state and covariance. These four functions are typically called in either of the orders

  * `correct!, combine!, interact!, predict!` (as is done in [`update!`](@ref))
  * `interact!, predict!, correct!, combine!` (as is done in the reference cited below)

These two orders are cyclic permutations of each other, and the order used in [`update!`](@ref) is chosen to align with the order used in the other filters, where the initial condition is corrected using the first measurement, i.e., we assume the first measurement updates $x(0|-1)$ to $x(0|0)$.

The initial (combined) state and covariance of the IMM filter is made up of the weighted average of the states and covariances of the individual filters. The weights are the initial mixing probabilities `μ`.

Ref: "Interacting multiple model methods in target tracking: a survey", E. Mazor; A. Averbuch; Y. Bar-Shalom; J. Dayan

# Arguments:

  * `models`: An array of Kalman-type filters, such as [`KalmanFilter`](@ref), [`ExtendedKalmanFilter`](@ref), [`UnscentedKalmanFilter`](@ref), etc. The state of each model must have the same meaning, such that forming a weighted average makes sense.
  * `P`: The mode-transition probability matrix. `P[i,j]` is the probability of transitioning from mode `i` to mode `j` (each row must sum to one).
  * `μ`: The initial mixing probabilities. `μ[i]` is the probability of being in mode `i` at the initial contidion (must sum to one).
  * `check`: If `true`, check that the inputs are valid. If `false`, skip the checks.
  * `p`: Parameters for the filter. NOTE: this `p` is shared among all internal filters. The internal `p` of each filter will be overridden by this one.
  * `interact`: If `true`, the filter will run the interaction as part of [`update!`](@ref) and [`forward_trajectory`](@ref). If `false`, the filter will not run the interaction step. This choice can be overridden by passing the keyword argument `interact` to the respective functions.
