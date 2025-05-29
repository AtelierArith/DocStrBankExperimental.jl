```
batchseq(seqs, val = 0)
```

Take a list of `N` sequences, and turn them into a single sequence where each item is a batch of `N`. Short sequences will be padded by `val`.

# Examples

```jldoctest
julia> batchseq([[1, 2, 3], [4, 5]], 0)
3-element Vector{Vector{Int64}}:
 [1, 4]
 [2, 5]
 [3, 0]
```
