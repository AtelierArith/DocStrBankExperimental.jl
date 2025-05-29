```
mle(prob::LikelihoodProblem, alg, args...; kwargs...)
mle(prob::LikelihoodProblem, alg::Tuple, args...; kwargs...)
```

Given the likelihood problem `prob` and an optimiser `alg`, finds the MLEs and returns a  [`LikelihoodSolution`](@ref) object. Extra arguments and keyword arguments for `solve` can be passed  through `args...` and `kwargs...`.

If `alg` is a `Tuple`, then the problem is re-optimised after each algorithm with the next element in alg,  starting from `alg[1]`, with initial estimate coming from the solution with the  previous algorithm (starting with `get_initial_estimate(prob)`).
