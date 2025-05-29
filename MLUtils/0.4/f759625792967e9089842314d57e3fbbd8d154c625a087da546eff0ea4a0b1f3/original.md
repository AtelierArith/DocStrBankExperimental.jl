```
kfolds(n::Integer, k = 5) -> Tuple
```

Compute the train/validation assignments for `k` repartitions of `n` observations, and return them in the form of two vectors. The first vector contains the index-vectors for the training subsets, and the second vector the index-vectors for the validation subsets respectively. A general rule of thumb is to use either `k = 5` or `k = 10`. 

Each observation is assigned to the validation subset once (and only once). Thus, a union over all validation index-vectors reproduces the full range `1:n`. Note that there is no random assignment of observations to subsets, which means that adjacent observations are likely to be part of the same validation subset.

# Examples

```jldoctest
julia> train_idx, val_idx = kfolds(10, 5);

julia> train_idx
5-element Vector{Vector{Int64}}:
 [3, 4, 5, 6, 7, 8, 9, 10]
 [1, 2, 5, 6, 7, 8, 9, 10]
 [1, 2, 3, 4, 7, 8, 9, 10]
 [1, 2, 3, 4, 5, 6, 9, 10]
 [1, 2, 3, 4, 5, 6, 7, 8]

julia> val_idx
5-element Vector{UnitRange{Int64}}:
 1:2
 3:4
 5:6
 7:8
 9:10
```
