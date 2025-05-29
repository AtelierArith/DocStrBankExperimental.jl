```
bo!(problem::BossProblem{Function}; kwargs...)
x = bo!(problem::BossProblem{Missing}; kwargs...)
```

Run the Bayesian optimization procedure to solve the given optimization problem or give a recommendation for the next evaluation point if `problem.f == missing`.

# Arguments

  * `problem::BossProblem`: Defines the optimization problem.

# Keywords

  * `model_fitter::ModelFitter`: Defines the algorithm used to estimate model parameters.
  * `acq_maximizer::AcquisitionMaximizer`: Defines the algorithm used to maximize the acquisition function.
  * `acquisition::AcquisitionFunction`: Defines the acquisition function maximized to select       promising candidates for further evaluation.
  * `term_cond::TermCond`: Defines the termination condition.
  * `options::BossOptions`: Defines miscellaneous settings.

# References

[`BossProblem`](@ref), [`ModelFitter`](@ref), [`AcquisitionMaximizer`](@ref), [`TermCond`](@ref), [`BossOptions`](@ref)

# Examples

See 'https://soldasim.github.io/BOSS.jl/stable/example/' for example usage.
