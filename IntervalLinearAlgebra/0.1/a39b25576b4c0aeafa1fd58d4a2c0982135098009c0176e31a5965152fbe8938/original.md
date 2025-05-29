```
HansenBliekRohn <: AbstractDirectSolver
```

Type for the `HansenBliekRohn` solver of the square interval linear system $Ax=b$. For more details see section 5.6.2 of [[HOR19]](@ref)

### Notes

  * Hansen-Bliek-Rohn works with H-matrices without precondition and with strongly regular matrices using [`InverseMidpoint`](@ref) precondition
  * If the midpoint of $A$ is a diagonal matrix, then the algorithm returns the exact hull.
  * An object of type Hansen-Bliek-Rohn is a callable function with method

    ```
      (hbr::HansenBliekRohn)(A::AbstractMatrix{T},
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

julia> hbr = HansenBliekRohn()
HansenBliekRohn linear solver

julia> hbr(A, b)
2-element Vector{Interval{Float64}}:
 [-1.66667, 1.66667]
 [-1.33334, 1.33334]
```
