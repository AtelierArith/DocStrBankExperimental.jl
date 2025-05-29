```
JointSurvivalModel <: HazardBasedDistribution <: ContinuousUnivariateDistribution
```

`JointSurvivalModel` is based on the hazard formulation:

$h_i(t) = h_0(t) \exp\left(\gamma' \cdot L(M_i (t)) + \beta' \cdot x \right),$

where $h_0: \mathbb{R} \to \mathbb{R}_{+}$ is the baseline hazard function. The term $L(M(t)): \mathbb{R} \to \mathbb{R}^k, k\in\mathbb{N}$ represents the link to the longitudinal model(s)  and $\gamma\in\mathbb{R}^k$ are the link coefficients. Lastly $x \in\mathbb{R}^l, l\in\mathbb{N}$ the covariates with coefficients $\beta\in\mathbb{R}^l$.

# Fields:

  * `h₀::Function`: a positive valued function in time representing the baseline hazard
  * `γ::Vector{Real}`: coefficients for links to longitudinal models, should have the same length as `link_m`
  * `link_m::Vector{Function}`: unary functions (one argument) in time representing the link to a single or multiple longitudinal models
  * `β::Vector{Real}`: coefficients for covariates, should have the same length as `x`
  * `x::Vector{Real}`: covariates

# Example

There are constructors for calling `JointSurvivalModel` without covariates and for single longitudinal models without the need for arrays. For example:

```
using JointSurvivalModels

JointSurvivalModel(identity, 0.01, identity, 0.02, 3)
# corresponds to hazard: identity(t) * exp(0.01 * identity(t) +  0.02 * 3) 
JointSurvivalModel(identity, 0.01, identity)
# corresponds to hazard: identity(t) * exp(0.01 * identity(t))
JointSurvivalModel(identity,
                    [0.01,-0.02,0.03],
                    [x -> sqrt(x), x -> sin(x)+1, x -> cos(x)^2],
                    [2, 0.3],
                    [ 0, sqrt(2)])
# corresponds to hazard: identity(t) * exp(0.01 * sqrt(t) - 0.02 * (sin(t)+1) + 0.03 * cos(t)^2  + 2 * 0 + 0.3 * sqrt(2))
```
