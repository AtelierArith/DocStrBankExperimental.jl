```
show_bipartition(n::Int64, idx::Int64)
```

Show the bipartition with a given index for a given number of taxa.

# Arguments

  * `n`: the number of taxa.
  * `idx`: the bipartition to show.

# Output

The `idx`-th bipartiion of trees with `n` taxa.

# Example:

```jldoctest
julia> show_bipartition(4, 3)
idx	partition
3	4 | 1 2 3 
```
