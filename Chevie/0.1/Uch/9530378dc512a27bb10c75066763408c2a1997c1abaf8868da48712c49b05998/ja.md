`deligne_lusztigCharTable(W)` または `dlCharTable(W)`

各共役類 `W` に対して、`R_{T_w}^G` の非可換文字の分解を与えます。

```julia-repl
julia> dlCharTable(W)
6×10 Matrix{Int64}:
 1   1   1   1   2   2   0   0   0   0
 1  -1   1  -1   0   0   0   0   0   0
 1  -1  -1   1   0   0   0   0   0   0
 1   1   0   0  -1   0   1   0   1   1
 1   1   0   0   0  -1   0   1  -1  -1
 1   1  -1  -1   0   0  -2  -2   0   0
```
