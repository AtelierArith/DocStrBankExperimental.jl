```
cover_digraph(p::Poset{T}) where {T}
```

ポゼット `p` の同じ頂点を持つ有向グラフを作成します。このグラフでは、`v` が `p` の中で `w` によって被覆されるときに限り、`v` から `w` への辺があります。
