```
mgvi_step(
    forward_model, data, n_residuals::Integer, center_init::AbstractVector{<:Real},
    config::MGVIConfig, context::MGVIContext
)
```

Performs one MGVI step and returns a tuple `(result::MGVIResult, updated_center::AbstractVector{<:Real})`.

Returns a tuple `(result::MGVIResult, updated_center::AbstractVector{<:Real})`.

The posterior distribution is approximated with a multivariate normal distribution. The covariance is approximated with the inverse Fisher information valuated at `center_init`. Samples are drawn according to this covariance, which are then used to estimate and minimize the KL divergence between the true posterior and the approximation.

Note: The prior is implicit, it is a standard (uncorrelated) multivariate normal distribution of the same dimensionality as `center_init`.

# Example

```julia
using Random, Distributions, MGVI
import LinearSolve, Zygote

context = MGVIContext(ADSelector(Zygote))

model(x::AbstractVector) = Normal(x[1], 0.2)
true_param = [2.0]
data = rand(model(true_param), 1)[1]
center = [1.3]

config = MGVIConfig(
    linsolver = LinearSolve.KrylovJL_CG(),
    optimizer = MGVI.NewtonCG()
)
n_residuals = 12
n_steps = 5

res, center = mgvi_step(model, data, n_residuals, center, config, context)
for i in 1:n_steps-1
    res, center = mgvi_step(model, data, n_residuals, center, config, context)
end

samples_from_est_covariance = res.samples
```
