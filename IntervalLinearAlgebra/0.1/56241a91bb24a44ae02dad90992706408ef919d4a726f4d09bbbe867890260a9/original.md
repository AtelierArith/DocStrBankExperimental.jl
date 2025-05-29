```
is_strictly_diagonally_dominant(A::AbstractMatrix{T}) where {T<:Interval}
```

Checks whether the square interval matrix $A$ of order $n$ is stictly diagonally dominant, that is if $mig(Aᵢᵢ) > ∑_{k ≠ i} mag(Aᵢₖ)$ for $i=1,…,n$. For more details see section 4.5 of [[HOR19]](@ref).

### Examples

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> is_strictly_diagonally_dominant(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_strictly_diagonally_dominant(A)
false
```
