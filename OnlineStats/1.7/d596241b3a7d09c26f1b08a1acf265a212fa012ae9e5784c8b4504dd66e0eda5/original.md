```
StatLearn(args...; penalty=zero, rate=LearningRate())
```

Fit a model (via stochastic approximation) that is linear in the parameters.  The (offline) objective function that StatLearn approximately minimizes is

$(1/n) ∑ᵢ f(yᵢ, xᵢ'β) + ∑ⱼ λⱼ g(βⱼ),$

where $fᵢ$ are loss functions of a response variable and linear predictor, $λⱼ$s are nonnegative regularization parameters, and $g$ is a penalty function.

Use `StatLearn` with caution, as stochastic approximation algorithms are inherently noisy.

# Arguments

  * `loss = OnlineStats.l2regloss`: The loss function to be (approximately) minimized.

      * Regression Losses:

          * `l2regloss`: Squared error loss
          * `l1regloss`: Absolute error loss
      * Classification (y ∈ {-1, 1}) Losses:

          * `logisticloss`: Logistic regression
          * `l1hingeloss`: Loss function used in Support Vector Machines.
          * `DWDLoss(q)`: Generalized Distance Weighted Discrimination (smoothed `l1hingeloss`)
  * `algorithm = MSPI()`: The stochastic approximation method to be used.

      * Algorithms based on Stochastic gradient:

          * `SGD()`: Stochastic Gradient Descent
          * `ADAGRAD()`: AdaGrad (adaptive version of SGD)
          * `RMSPROP()`: RMSProp (adaptive version of SGD)
      * Algorithms based on Majorization-Minimization Principle:

          * `MSPI()`: Majorized Stochastic Proximal Iteration
          * `OMAS()`: Online MM via Averaged Surrogate
          * `OMAP()`: Online MM via Averaged Parameter
  * `λ = 0.0`: The hyperparameter(s) used for the penalty function

      * User can provide elementwise penalty hyperparameters (`Vector{Float64}`) or single hyperparameter (`Float64`).

## Keyword Arguments

  * `penalty`: The regularization function used.

      * `zero`: no penalty (default)
      * `abs`: (LASSO) parameters penalized by their absolute value
      * `abs2`: (Ridge) parameters penalized by their squared value
      * `ElasticNet(α)`: α * (abs penalty) + (1-α) * (abs2 penalty)
  * `rate = LearningRate(.6)`

# Example

```
x = randn(1000, 5)
y = x * range(-1, stop=1, length=5) + randn(1000)

o = fit!(StatLearn(MSPI()), zip(eachrow(x), y))
coef(o)

o = fit!(StatLearn(OnlineStats.l1regloss, ADAGRAD()), zip(eachrow(x), y))
coef(o)
```
