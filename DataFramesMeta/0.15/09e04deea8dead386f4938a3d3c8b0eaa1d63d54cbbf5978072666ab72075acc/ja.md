```
@kwarg(args...)
```

DataFramesMeta.jl マクロ内で、引数が「ブロック」形式で書かれているときに、基盤となる DataFrames.jl 関数にキーワード引数を渡します。

```
julia> df = DataFrame(x = [1, 1, 2, 2], b = [5, 6, 7, 8]);

julia> @rsubset df begin
           :x == 1
           @kwarg view = true
       end
2×2 SubDataFrame
 Row │ x      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      5
   2 │     1      6
```

!!! note
    これは DataFramesMeta.jl マクロ内でのみ意味があります。DataFrames.jl マクロの外では機能しません。

