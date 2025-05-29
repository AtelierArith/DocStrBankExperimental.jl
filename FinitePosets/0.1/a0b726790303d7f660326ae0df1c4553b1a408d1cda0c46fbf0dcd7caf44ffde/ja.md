`moebius_matrix(P::CPoset)` は Moebius 関数 `μ(x,y)` の行列（ζ またはインシデンス行列の逆）です。

```julia-repl
julia> moebius_matrix(CPoset(:diamond,5))
5×5 Matrix{Int64}:
 1  -1  -1  -1   2
 0   1   0   0  -1
 0   0   1   0  -1
 0   0   0   1  -1
 0   0   0   0   1
```

`moebius_matrix(P::Poset)` は `moebius_matrix(P.C)` を返します。
