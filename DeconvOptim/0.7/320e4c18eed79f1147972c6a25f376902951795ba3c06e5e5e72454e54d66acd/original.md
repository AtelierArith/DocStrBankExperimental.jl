```
TV_cuda(; num_dims=2)
```

This function returns a function to calculate the Total Variation regularizer  of a 2 or 3 dimensional array. `num_dims` can be either `2` or `3`.

```julia-repl
julia> using CUDA

julia> reg = TV_cuda(num_dims=2);

julia> reg(CuArray([1 2 3; 4 5 6; 7 8 9]))
12.649111f0
```
