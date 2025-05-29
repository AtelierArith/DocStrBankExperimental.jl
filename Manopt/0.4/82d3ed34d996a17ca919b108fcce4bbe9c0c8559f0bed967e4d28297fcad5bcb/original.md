```
FrankWolfeState <: AbstractManoptSolverState
```

A struct to store the current state of the [`Frank_Wolfe_method`](@ref)

It comes in two forms, depending on the realisation of the `subproblem`.

# Fields

  * `p`:                         the current iterate, a point on the manifold
  * `X`:                         the current gradient $\operatorname{grad} F(p)$, a tangent vector to `p`.
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) an inverse retraction method to use within Frank Wolfe.
  * `sub_problem`:               an [`AbstractManoptProblem`](@ref) problem or a function `(M, p, X) -> q` or `(M, q, p, X)` for the a closed form solution of the sub problem
  * `sub_state`:                 an [`AbstractManoptSolverState`](@ref) for the subsolver or an [`AbstractEvaluationType`](@ref) in case the sub problem is provided as a function
  * `stop`:                      ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`) a [`StoppingCriterion`](@ref)
  * `stepsize`:                  ([`DecreasingStepsize`](@ref)`(; length=2.0, shift=2)`) $s_k$ which by default is set to $s_k = \frac{2}{k+2}$.
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) a retraction to use within Frank-Wolfe

The sub task requires a method to solve

$$
   \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

# Constructor

```
FrankWolfeState(M, p, X, sub_problem, sub_state)
```

where the remaining fields from before are keyword arguments.
