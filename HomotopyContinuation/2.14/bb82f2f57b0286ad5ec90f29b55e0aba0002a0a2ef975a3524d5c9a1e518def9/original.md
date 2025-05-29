```
SemialgebraicSetsHCSolver(; excess_residual_tol = nothing, real_tol = 1e-6, compile = false, options...)
```

Construct a `SemialgebraicSets.AbstractAlgebraicSolver` to be used in `SemialgebraicSets`. `options` are all valid options for [`solve`](@ref).

Solutions with imaginary part of absolute value larger than `real_tol` are filtered out.

For overdetermined systems, `excess_residual_tol` can be set to a `Float64` value. Excess solutions that have a residual smaller than `excess_residual_tol` are reconsidered as a success.

## Example

```
julia> using HomotopyContinuation, SemialgebraicSets;

julia> solver = SemialgebraicSetsHCSolver(; show_progress = false)
SemialgebraicSetsHCSolver(; compile = :none, show_progress = false)

julia> @polyvar x y
(x, y)

julia> V = @set x^2 == 1 && y^2 == 2 solver
Algebraic Set defined by 2 equalities
 x^2 - 1.0 = 0
 y^2 - 2.0 = 0

julia> collect(V)
4-element Array{Array{Float64,1},1}:
 [1.0, 1.414213562373095]
 [1.0, -1.414213562373095]
 [-1.0, 1.414213562373095]
 [-1.0, -1.414213562373095]
```
