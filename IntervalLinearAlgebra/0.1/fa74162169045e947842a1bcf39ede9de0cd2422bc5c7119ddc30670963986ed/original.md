```
solve(A::AbstractMatrix{T},
      b::AbstractVector{T},
      solver::AbstractIterativeSolver,
      [precondition]::AbstractPrecondition=_default_precondition(A, solver),
      [X]::AbstractVector{T}=enclose(A, b)) where {T<:Interval}
```

Solves the square interval system $Ax=b$ using the given algorithm, preconditioner and initial enclosure

### Input

  * `A` – square interval matrix
  * `b` – interval vector
  * `solver` – algorithm used to solve the linear system
  * `precondition` – preconditioner used. If not given, it is automatically computed based on                   the matrix `A` and the solver.
  * `X` – initial enclosure.        if not given, it is automatically computed using [`enclose`](@ref)

### Examples

```jldoctest
julia> A = [2..4 -1..1;-1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> b = [-2..2, -1..1]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-1, 1]

julia> solve(A, b, GaussSeidel(), NoPrecondition(), [-10..10, -10..10])
2-element Vector{Interval{Float64}}:
 [-1.66668, 1.66668]
 [-1.33334, 1.33334]

julia> solve(A, b, GaussSeidel())
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]
```
