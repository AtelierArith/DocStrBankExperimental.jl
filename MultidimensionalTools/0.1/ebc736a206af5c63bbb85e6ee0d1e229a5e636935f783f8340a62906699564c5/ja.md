指定された値を指定された次元に沿って n 回繰り返します。

```julia
julia> A = rand(Int8, 2, 2)
2×2 Array{Int8,2}:
  28  23
 -47  54

julia> append_n_times(A, 2, Int8(3), dims = 1) # 値 3 を最初の次元に沿って 2 回繰り返す
4×2 Array{Int8,2}:
  28  23
 -47  54
   3   3
   3   3
```
