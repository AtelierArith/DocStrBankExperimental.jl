```julia
julia> A = rand(Int8, 2, 2)
2×2 Array{Int8,2}:
  28  23
 -47  54

julia> append_n_times_backwards(A, 2, Int8(3), dims = 1) # 1次元に沿って値3を2回繰り返す
4×2 Array{Int8,2}:
  3   3
  3   3
  28  23
 -47  54
```
