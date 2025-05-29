```
lastinds(ic::Vector{Int})
```

Returns a vector of integers containing the last index position of each unique value in the input integer vector `ic`.

When operating on the output returned from `groupinds(unique(A, dim))`, the returned vector of integers correspond to the positions of the last of each unique slice present in the original input multidimensional array `A` along dimension `dim`.

The implementation of `firstinds` accepting a vector of vector of integers operates on the output returned from `groupinds(ic::Vector{Int})`.
