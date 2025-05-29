```
comparison_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

Computes the comparison matrix $⟨A⟩$ of the given interval matrix $A$ according to the definition $⟨A⟩ᵢᵢ = mig(Aᵢᵢ)$ and $⟨A⟩ᵢⱼ = -mag(Aᵢⱼ)$ if $i≠j$.

### Examples

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> comparison_matrix(A)
2×2 Matrix{Float64}:
  2.0  -1.0
 -1.0   2.0
```
