`Poset(p::CPoset,e::AbstractVector=1:length(p))`

は、`p` によって指定された順序と要素 `e` を持つ `Poset` を作成します。

```julia-repl
julia> Poset(CPoset([[2,3],[4],[4],Int[]]),[:a,:b,:c,:d])
a<b,c<d
```

第二引数なしで `CPoset` を `Poset` に変換します。
