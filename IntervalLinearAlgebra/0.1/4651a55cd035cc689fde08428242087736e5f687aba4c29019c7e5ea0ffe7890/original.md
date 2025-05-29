```
LinearOettliPrager <: AbstractDirectSolver
```

Type for the OettliPrager solver of the interval linear system $Ax=b$. The solver first converts the system of interval equalities into a system of real inequalities using Oettli-Präger theorem [[OET64]](@ref) and then finds the feasible set by solving a LP problem in each orthant using `LazySets.jl`.

### Notes

  * You need to import `LazySets.jl` to use this functionality.
  * An object of type `LinearOettliPrager` is a function with methods

    ```
      (op::LinearOettliPrager)(A::AbstractMatrix{T},
                               b::AbstractVector{T}) where {T<:Interval}
    ```

    #### Input

      * `A`   – N×N interval matrix
      * `b`   – interval vector of length N

### Examples

```julia-repl
julia> A = [2..4 -2..1;-1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> b = [-2..2, -2..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-2, 2]

julia> polytopes = solve(A, b, LinearOettliPrager());

julia> typeof(polytopes)
Vector{HPolytope{Float64, SparseArrays.SparseVector{Float64, Int64}}}
```
