```
firstinds(ic::Vector{Int})
firstinds(ib::Vector{Vector{Int}})
```

Returns a vector of integers containing the first index position of each unique value in the input integer vector `ic`, or the first index position of each entry in the input vector of integer vectors `ib`.

When operating on the output returned from `unique(A, dim)`, the returned vector of integers correspond to the positions of the first of each unique slice present in the original input multidimensional array `A` along dimension `dim`.

The implementation of `firstinds` accepting a vector of integers operates on the output returned from `groupslices(A, dim)`.

The implementation of `firstinds` accepting a vector of vector of integers operates on the output returned from `groupinds(ic::Vector{Int})`.
