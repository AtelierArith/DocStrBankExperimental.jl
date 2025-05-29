```julia
struct EnsembleProblem{T, T2, T3, T4, T5} <: SciMLBase.AbstractEnsembleProblem
```

Main constructor for `EnsembleProblem`.

## Keyword Arguments

  * `prob`: The base problem.
  * `prob_func`: Function to modify the base problem per trajectory.
  * `output_func`: Function to extract output from a solution.
  * `reduction`: Function to aggregate results.
  * `u_init`: Initial value for aggregation.
  * `safetycopy`: Whether to deepcopy the problem before modifying.
