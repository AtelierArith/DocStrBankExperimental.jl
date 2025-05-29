```julia
bifurcationdiagram(
    prob,
    alg,
    level,
    options;
    linear_algo,
    kwargs...
)

```

Compute the bifurcation diagram associated with the problem `F(x, p) = 0` recursively.

# Arguments

  * `prob::AbstractBifurcationProblem` bifurcation problem
  * `alg` continuation algorithm
  * `level` maximum branching (or recursion) level for computing the bifurcation diagram
  * `options = (x, p, level) -> contparams` this function allows to change the [`continuation`](@ref) options depending on the branching `level`. The argument `x, p` denotes the current solution to `F(x, p)=0`.
  * `kwargs` optional arguments. Look at [`bifurcationdiagram!`](@ref) for more details.

# Simplified call:

We also provide the method

`bifurcationdiagram(prob, br::ContResult, level::Int, options; kwargs...)`

where `br` is a branch computed after a call to [`continuation`](@ref) from which we want to compute the bifurcating branches recursively.
