```
InverseMidpoint <: AbstractPrecondition
```

Preconditioner that preconditions the linear system $Ax=b$ with $A_c^{-1}$, where $A_c$ is the midpoint matrix of $A$.

### Notes

  * An object of type `InverseMidpoint` is a function with method

    ```
      (imp::InverseMidpoint)(A::AbstractMatrix{T},
                             b::AbstractVector{T}) where {T<:Interval}
    ```

### Examples

```jldoctest
julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> b = [-2..2, -2..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-2, 2]

julia> imp = InverseMidpoint()
InverseMidpoint()

julia> imp(A, b)
(Interval{Float64}[[0.594594, 1.40541] [-0.540541, 0.540541]; [-0.540541, 0.540541] [0.594594, 1.40541]], Interval{Float64}[[-0.756757, 0.756757], [-0.756757, 0.756757]])
```
