```
inrangecount(ss, query, r::Real; kwargs....) → n::Int
```

検索構造 `ss` の中で、`query` の範囲 `r` 内にあるポイントの数 `n` をカウントします。通常、`WithinRange(r)` を使って [`search`](@ref) の `length` を取得するよりもパフォーマンスが良いです。
