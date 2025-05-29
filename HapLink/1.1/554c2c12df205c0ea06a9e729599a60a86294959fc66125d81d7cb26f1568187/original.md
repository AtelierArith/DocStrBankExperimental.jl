```
significance(counts::AbstractArray{<:Integer})
```

Calculates the $χ^2$ significance of a haplotype given its $N$-dimensional contingency matrix, `counts`

See the documentation on [`linkage(::AbstractArray{<:Integer})`](@ref) or [`occurrence_matrix`](@ref) for details on how `counts` should be constructed.
