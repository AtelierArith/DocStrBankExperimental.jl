`Poset(covers::Vector{Tuple{T,T}}) where T`

は、与えられた関係の推移的閉包を表す部分順序集合（poset）を作成します。部分順序集合は、関係に現れる要素の上にあります。

```julia-repl
julia> Poset([(:a,:b),(:d,:c)])
a<b
d<c
```
