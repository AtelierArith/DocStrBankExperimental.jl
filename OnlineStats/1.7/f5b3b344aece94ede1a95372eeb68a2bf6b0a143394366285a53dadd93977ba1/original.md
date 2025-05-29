```
DPMM(comp_mu::Real,
     comp_lambda::Real,
     comp_alpha::Real,
     comp_beta::Real,
     dirichlet_alpha::Real;
     comp_birth_thres=1e-2,
     comp_death_thres=1e-2,
     n_comp_max=10)
```

Online univariate dirichlet process Gaussian mixture model algorithm.

# Mathematical Description

The model is described as

```
G ~ DP(dirchlet_alpha, Normal-Gamma)
(μₖ, τₖ) ~ G
x ~ N(μ, 1/sqrt(τ))
```

where the base measure is defined as

```
τₖ ~ Gamma(comp_alpha, 1/comp_beta)
μₖ ~ N(comp_mu, 1/sqrt(comp_lambda*τₖ)).
```

The variational distribution is the mean-field family defined as

```
q(μₖ | τₖ; mₖ, lₖ) q(τₖ; aₖ, bₖ) = N(μₖ; mₖ, 1/(lₖ*τₖ)) Gamma(τₖ; aₖ, 1/bₖ).
```

Since the model is nonparametric, mixture components are added depending on the birth threshold `comp_birth_thres` (higher means less frequen births) and  existing components are pruned depending on the death threshold `comp_death_thres`.

# Hyperparameters

DPMMs tend to be very sensitive to its hyperparameters. Therefore, it is important to monitor the fitted result and tweak the hyperparameters accordingly. Here are the implications of each hyperparameter:

  * `comp_mu`: Prior mean of the components
  * `comp_lambda`: Prior precision of the components. This affects the dispersion                of the components relative to the scale of each component.                (Smaller the more dispersed.) (`comp_lambda` > 0)
  * `comp_alpha`: Gamma shape parameter of the scale (inverse of the variance) of               each component. (`comp_alpha` > 0)
  * `comp_beta`: Gamma scale parameter of the scale (inverse of the variance) of              each component. (`comp_beta` > 0)
  * `dirichlet_alpha`: Initial weight of a newly added component. Larger values                    result in more components being created.                    (`dirichlet_alpha` > 0)
  * `comp_birth_thres`: Threshold for adding a new component (highly affected by                     `dirichlet_alpha`)
  * `comp_death_thres`: Threshold for prunning (or killing) an existing component.

A mechanical procedure for setting the component hyperparameters is to first set `comp_alpha > 2`. This ensures the variance to be finite. Then, solve `comp_beta` such that the Gamma distribution concentrates most of the probability density on the expected range of `1/τₖ`, the variance of each component. Finally, solve for `comp_lambda` such that the marginal density of `μₖ`, which is a Student-T distribution

```
p(μₖ | λ₀, α₀, β₀)
    = ∫ p(μₖ | τₖ, μ₀, λ₀) p(τₖ | α₀, β₀) dτₖ
    = ∫ N(μₖ; μ₀, 1/sqrt(λ₀*τₖ)) Gamma(τₖ; αₖ, βₖ) dτₖ
    = TDist( 2*α₀, μ₀, sqrt(β₀/(λ₀*α₀)),
```

has its probability density concentrated on the expected range of the component means.

Below is a implementing the prior elicitation procedure described above:

```
using Roots

prob_τₖ = 0.8
τₖ_max  = 0.5
μ₀      = 0.0
α₀      = 2.1
prob_μₖ = 0.8
μₖ_min  = -2
μₖ_max  = 2

β₀ = find_zero(β₀ -> cdf(InverseGamma(α₀, β₀), τₖ_max) - prob_τₖ, (1e-4, Inf))
λ₀ = find_zero(λ₀ -> begin
    p_μ = TDist(2*α₀)*sqrt(β₀/(λ₀*α₀)) + μ₀
    cdf(p_μ, μₖ_max) - cdf(p_μ, μₖ_min) - prob_τₖ
end, (1e-4, 1e+2))
```

`prob_*` sets the amount of density on the desired range. `τₖ_max`, `μₖ_min`, `μₖ_max` is the expected range of each parameters. Since we leave `1 - prob_*` density on the tails, these are soft contraints.

Unfortunately, `dirichlet_alpha`, `comp_birth_thres`, `comp_death_thres` can be tuned only through trial and error. However, `dirichlet_alpha` is best set 0.5 ~ 1e-2 depending on the desired number of components.

# Example

```
n    = 1024
μ    = 0.0
λ    = 0.1
α    = 2.1
β    = 0.5
α_dp = 1.0
o    = DPMM(μ, λ, α, β, α_dp; comp_birth_thres=0.5,
            comp_death_thres=1e-2, n_comp_max=10) 
p = MixtureModel([ Normal(-2.0, 0.5), Normal(3.0, 1.0) ], [0.7, 0.3])
o = fit!(o, rand(p, 1000))
```
