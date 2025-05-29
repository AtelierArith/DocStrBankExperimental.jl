```
remove_duplicate_sequences(Z::Matrix{Ti}) where Ti<:Integer
```

Remove duplicate sequences (columns) in the alignment matrix `Z`

# Examples

```
julia> Z = [1 2 3 1;
            1 3 2 1;]
2×4 Array{Int64,2}:
 1  2  3  1
 1  3  2  1

julia> remove_duplicate_sequences(Z)
removing duplicate sequences... done: 4 -> 3
([1 2 3; 1 3 2], [1, 2, 3])
```
