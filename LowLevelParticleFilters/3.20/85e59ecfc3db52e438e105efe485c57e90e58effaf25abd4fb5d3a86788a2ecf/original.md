```
WikiParams(; α = 1.0, β = 0.0, κ = 1.0)
WikiParams(; ακ = 1.0, β = 0.0) # Simplified interface with only one parameter for ακ
```

Unscented transform parameters suggested at [Wiki: Kalman*filter#Sigma*points](https://en.wikipedia.org/wiki/Kalman_filter#Sigma_points).

  * `α`: Scaling parameter (0,1] for the spread of the sigma points. Reduce `α` to reduce the spread.
  * `β`: Incorporates prior knowledge of the distribution of the state.
  * `κ`: Secondary scaling parameter that is usually set to 3nx/2 or 1. Increase `κ` to increase the spread of the sigma points.

If $α^2 κ < L$ where $L$ is the dimension ofthe sigma points, the center mean weight is negative. This is allowed, but may in some cases lead to an indefinite covariance matrix.

The spread of the points are $α^2 κ$, that is, independent on the point dimension. Visualize the spread by

```julia
using Plots
μ = [0.0, 0.0]
Σ = [1.0 0.0; 0.0 1.0]
pars = LowLevelParticleFilters.WikiParams(α = 1.0, β = 0.0, κ = 1.0)
xs = LowLevelParticleFilters.sigmapoints(μ, Σ, pars)
unscentedplot(xs, pars)
```

A simplified tuning rule 

  * If a decrease in the spread of the sigma points is desired, use $κ = 1$ and $α < 1$.
  * If an increase in the spread of the sigma points is desired, use $κ > 1$ and $α = 1$.

This rule may be used when using the interface with only a single function argument $ακ$. See Nielsen, K. et al., 2021, "UKF Parameter Tuning for Local Variation Smoothing" for more details.

See also [`MerweParams`](@ref) and [`TrivialParams`](@ref)
