```
CompressedBeliefSolver
```

The `CompressedBeliefSolver` struct represents a solver for compressed belief-state MDPs. It combines a compressed belief-state MDP with a base solver to approximate the value function.

## Fields

  * `m::CompressedBeliefMDP`: The compressed belief-state MDP.
  * `base_solver::Solver`: The base solver used to solve the compressed belief-state MDP.

## Constructors

```
CompressedBeliefSolver(pomdp::POMDP, base_solver::Solver; updater::Updater=DiscreteUpdater(pomdp), sampler::Sampler=BeliefExpansionSampler(pomdp), compressor::Compressor=PCACompressor(1))
CompressedBeliefSolver(pomdp::POMDP; updater::Updater=DiscreteUpdater(pomdp), sampler::Sampler=BeliefExpansionSampler(pomdp), compressor::Compressor=PCACompressor(1), interp::Union{Nothing, LocalFunctionApproximator}=nothing, k::Int=1, verbose::Bool=false, max_iterations::Int=1000, n_generative_samples::Int=10, belres::Float64=1e-3)
```

Constructs a `CompressedBeliefSolver` using the specified POMDP, base solver, updater, sampler, and compressor. Alternatively, you can omit the base solver in which case a `LocalApproximationValueIterationSolver`(https://github.com/JuliaPOMDP/LocalApproximationValueIteration.jl) will be created instead. For example, different base solvers are needed if the POMDP state and action space are continuous.

## Example Usage

```julia-repl
julia> pomdp = TigerPOMDP();
julia> solver = CompressedBeliefSolver(pomdp; verbose=true, max_iterations=10);
julia> solve(solver, pomdp);
[Iteration 1   ] residual:       8.51 | iteration runtime:    635.870 ms, (     0.636 s total)
[Iteration 2   ] residual:       3.63 | iteration runtime:      0.504 ms, (     0.636 s total)
[Iteration 3   ] residual:       10.1 | iteration runtime:      0.445 ms, (     0.637 s total)
[Iteration 4   ] residual:       15.2 | iteration runtime:      0.494 ms, (     0.637 s total)
[Iteration 5   ] residual:       6.72 | iteration runtime:      0.432 ms, (     0.638 s total)
[Iteration 6   ] residual:       7.38 | iteration runtime:      0.508 ms, (     0.638 s total)
[Iteration 7   ] residual:       6.03 | iteration runtime:      0.495 ms, (     0.639 s total)
[Iteration 8   ] residual:       5.73 | iteration runtime:      0.585 ms, (     0.639 s total)
[Iteration 9   ] residual:       4.02 | iteration runtime:      0.463 ms, (      0.64 s total)
[Iteration 10  ] residual:       7.28 | iteration runtime:      0.576 ms, (      0.64 s total)
```
