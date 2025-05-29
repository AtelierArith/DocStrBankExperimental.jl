```
NoPrecondition <: AbstractPrecondition
```

Type of the trivial preconditioner which does nothing.

### Notes

  * An object of type `NoPrecondition` is a function with method

    ```
      (np::NoPrecondition)(A::AbstractMatrix{T},
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

julia> np = NoPrecondition()
NoPrecondition()

julia> np(A, b)
(Interval{Float64}[[2, 4] [-2, 1]; [-1, 2] [2, 4]], Interval{Float64}[[-2, 2], [-2, 2]])
```
