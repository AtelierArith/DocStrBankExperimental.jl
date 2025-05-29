`deligne_lusztigCharTable(W)` or `dlCharTable(W)`

for  each conjugacy class of `W`, gives the decomposition of `R_{T_w}^G` in unipotent characters.

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
