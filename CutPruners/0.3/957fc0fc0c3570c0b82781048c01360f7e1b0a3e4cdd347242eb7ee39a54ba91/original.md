```
exactpruning!(man::AbstractCutPruner, optimizer_constructor;
              ub=Inf, lb=-Inf, epsilon=1e-5)
```

Remove dominated cuts in CutPruner `man`.

We use a LP solver to determine whether a cut is dominated or not.

# Arguments

  * `man::AbstractCutPruner`   Cut pruner where to remove cuts
  * `optimizer_constructor`   Optimizer used to solve LP
  * `ub::Union{Float64, Vector{Float64}}`   State x upper bound
  * `lb::Union{Float64, Vector{Float64}}`   State x lower bound
  * `epsilon::Float64`   Pruning's tolerance
