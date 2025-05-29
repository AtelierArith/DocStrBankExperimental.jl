`CPoset(m::Matrix{Bool})`

インシデンス行列 `m` から部分順序集合を作成します。すなわち、`m[i,j]==true` である場合、部分順序集合において `i≤j` です。

```julia-repl
julia> CPoset(Bool[1 1 1 1 1;0 1 0 1 1;0 0 1 1 1;0 0 0 1 0;0 0 0 0 1])
1<2,3<4,5
```
