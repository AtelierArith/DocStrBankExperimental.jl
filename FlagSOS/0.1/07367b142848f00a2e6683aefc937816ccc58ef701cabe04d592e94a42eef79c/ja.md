```
glue(F::PartiallyColoredFlag{T}, G::PartiallyColoredFlag{T}, p::Vector{Int})
```

2つの部分的にラベル付けされたフラグ `F` と `G` を接合します。接合する前に、`F` の頂点に対して置換 `p` を適用します。`p` は `size(F)` よりも多くの頂点を含む置換であっても構いませんが、同じ色の頂点は同じ色の頂点に対応させる必要があります。
