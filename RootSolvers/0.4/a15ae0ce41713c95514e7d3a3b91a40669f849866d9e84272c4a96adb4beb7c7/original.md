```
RootSolvers
```

Contains functions for solving roots of non-linear equations. See [`find_zero`](@ref).

## Example

```julia
julia> using RootSolvers

julia> sol = find_zero(x -> x^2 - 100^2,
                       SecantMethod{Float64}(0.0, 1000.0),
                       CompactSolution());

julia> sol
CompactSolutionResults{Float64}:
├── Status: converged
└── Root: 99.99999999994358

julia> sol.root
99.99999999994358
```
