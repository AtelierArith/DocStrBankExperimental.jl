```
GaussianElimination <: AbstractDirectSolver
```

Type for the Gaussian elimination solver of the square interval linear system $Ax=b$. For more details see section 5.6.1 of [[HOR19]](@ref)

### Notes

  * An object of type `GaussianElimination` is a callable function with method

    ```
      (ge::GaussianElimination)(A::AbstractMatrix{T},
                                b::AbstractVector{T}) where {T<:Interval}
    ```

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

julia> ge = GaussianElimination()
GaussianElimination linear solver

julia> ge(A, b)
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]
```
