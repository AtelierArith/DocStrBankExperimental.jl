Repeats a specified value n many times along the specified dimension.

```julia
julia> A = rand(Int8, 2, 2)
2×2 Array{Int8,2}:
  28  23
 -47  54

julia> append_n_times(A, 2, Int8(3), dims = 1) # repeat the value 3 twice along the first dimension
4×2 Array{Int8,2}:
  28  23
 -47  54
   3   3
   3   3
```
