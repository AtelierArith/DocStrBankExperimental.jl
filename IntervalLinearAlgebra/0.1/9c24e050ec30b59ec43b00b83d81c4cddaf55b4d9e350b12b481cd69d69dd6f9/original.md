```
InverseDiagonalMidpoint <: AbstractPrecondition
```

Preconditioner that preconditions the linear system $Ax=b$ with the diagonal matrix of $A_c^{-1}$, where $A_c$ is the midpoint matrix of $A$.

### Notes

  * An object of type `InverseDiagonalMidpoint` is a function with method

    ```
      (idmp::InverseDiagonalMidpoint)(A::AbstractMatrix{T},
                                      b::AbstractVector{T}) where {T<:Interval}
    ```

### Example

```jldoctest
julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> b = [-2..2, -2..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-2, 2]

julia> idmp = InverseDiagonalMidpoint()
InverseDiagonalMidpoint()

julia> idmp(A, b)
(Interval{Float64}[[0.666666, 1.33334] [-0.666667, 0.333334]; [-0.333334, 0.666667] [0.666666, 1.33334]], Interval{Float64}[[-0.666667, 0.666667], [-0.666667, 0.666667]])
```
