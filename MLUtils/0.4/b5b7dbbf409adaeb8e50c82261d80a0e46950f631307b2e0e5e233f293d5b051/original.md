```
leavepout(n::Integer, [size = 1]) -> Tuple
```

Compute the train/validation assignments for `k ≈ n/size` repartitions of `n` observations, and return them in the form of two vectors. The first vector contains the index-vectors for the training subsets, and the second vector the index-vectors for the validation subsets respectively. Each validation subset will have either `size` or `size+1` observations assigned to it. The following code snippet generates the index-vectors for `size = 2`.

```julia
julia> train_idx, val_idx = leavepout(10, 2);
```

Each observation is assigned to the validation subset once (and only once). Thus, a union over all validation index-vectors reproduces the full range `1:n`. Note that there is no random assignment of observations to subsets, which means that adjacent observations are likely to be part of the same validation subset.

```julia
julia> train_idx
5-element Array{Array{Int64,1},1}:
 [3,4,5,6,7,8,9,10]
 [1,2,5,6,7,8,9,10]
 [1,2,3,4,7,8,9,10]
 [1,2,3,4,5,6,9,10]
 [1,2,3,4,5,6,7,8]

julia> val_idx
5-element Array{UnitRange{Int64},1}:
 1:2
 3:4
 5:6
 7:8
 9:10
```
