```
AdaptiveRegularizationState{P,T} <: AbstractHessianSolverState
```

A state for the [`adaptive_regularization_with_cubics`](@ref) solver.

# Fields

a default value is given in brackets if a parameter can be left out in initialization.

  * `η1`, `η2`:           (`0.1`, `0.9`) bounds for evaluating the regularization parameter
  * `γ1`, `γ2`:           (`0.1`, `2.0`) shrinking and expansion factors for regularization parameter `σ`
  * `p`:                  (`rand(M)` the current iterate
  * `X`:                  (`zero_vector(M,p)`) the current gradient $\operatorname{grad}f(p)$
  * `s`:                  (`zero_vector(M,p)`) the tangent vector step resulting from minimizing the model problem in the tangent space $\mathcal T_{p} \mathcal M$
  * `σ`:                  the current cubic regularization parameter
  * `σmin`:               (`1e-7`) lower bound for the cubic regularization parameter
  * `ρ_regularization`:   (`1e3`) regularization parameter for computing ρ.

When approaching convergence ρ may be difficult to compute with numerator and denominator approaching zero.  Regularizing the ratio lets ρ go to 1 near convergence.

  * `evaluation`:         (`AllocatingEvaluation()`) if you provide a
  * `retraction_method`:  (`default_retraction_method(M)`) the retraction to use
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(100)`) a [`StoppingCriterion`](@ref)
  * `sub_problem`:        sub problem solved in each iteration
  * `sub_state`:          an [`AbstractManoptSolverState`](@ref) for the subsolver

Furthermore the following integral fields are defined

  * `q`:                  (`copy(M,p)`) a point for the candidates to evaluate model and ρ
  * `H`:                  (`copy(M, p, X)`) the current Hessian, $\operatorname{Hess}F(p)[⋅]$
  * `S`:                  (`copy(M, p, X)`) the current solution from the subsolver
  * `ρ`:                  the current regularized ratio of actual improvement and model improvement.
  * `ρ_denominator`:      (`one(ρ)`) a value to store the denominator from the computation of ρ to allow for a warning or error when this value is non-positive.

# Constructor

```
AdaptiveRegularizationState(M, p=rand(M); X=zero_vector(M, p); kwargs...)
```

Construct the solver state with all fields stated as keyword arguments.
