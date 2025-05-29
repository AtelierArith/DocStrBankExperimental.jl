```
create_random_filter(lc::LefschetzComplex)
```

Create a random injective filter on a Lefschetz complex.

The function creates a random injective filter on a Lefschetz complex. The filter is created by assigning integers to cell groups, increasing with dimension. Within each dimension the assignment is random, but all filter values of cells of dimension `k` are less than all filter values of cells with dimension `k+1`. The function returns the filter as `Vector{Int}`, with indices corresponding to the cell indices in the Lefschetz complex.
