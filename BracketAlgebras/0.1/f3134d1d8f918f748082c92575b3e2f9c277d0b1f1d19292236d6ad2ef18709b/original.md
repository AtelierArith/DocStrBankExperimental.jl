Tabloid(matrix::AbstractMatrix{<:Integer}, ordering::AbstractVector{<:Integer}=collect(1:maximum(matrix)))

Return the tabloid whose rows correspond to the rows of matrix with the given ordering. The entries of the rows are sorted wrt the ordering and then the rows are ordered lexicographically (tableaux order).

# Examples

```jldoctest
julia> Tabloid([4 2 1; 3 1 4], [3,1,2,4])
[3 1 4; 1 2 4]
```

```jldoctest
julia> Tabloid([4 2 1; 3 1 4], [3,2,4,1])
[3 4 1; 2 4 1]
```
