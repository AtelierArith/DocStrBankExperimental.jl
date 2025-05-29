```
Crash
```

Collection of crash methods used to generate initial decisions in structured algorithms.

...

# Available crash methods

  * [`None`](@ref)
  * [`EVP`](@ref)
  * [`Scenario`](@ref)
  * [`Custom`](@ref)

...

## Examples

The following solves a stochastic program `sp` created in `StochasticPrograms.jl` using an L-shaped algorithm with trust-region and Clp as an `lpsolver` and by generating an initial decision with the `EVP` crash.

```jldoctest
julia> optimize!(sp, solver = LShapedSolver(GLPKSolverLP(), crash=Crash.EVP(), regularize = TrustRegion()))
L-Shaped Gap  Time: 0:00:00 (8 iterations)
  Objective:       -855.8333333333339
  Gap:             0.0
  Number of cuts:  4
  Iterations:      8
:Optimal
```
