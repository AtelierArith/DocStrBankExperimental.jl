```
eliminate!(G::AbstractGraph, v::Integer, c_map::Dict{Int, Int})
```

vの隣接点をすべて接続してから、Gからvを削除します。

辞書`c_map`は、'G'の頂点をそのクリーク性にマッピングし、適宜インプレースで更新されます。
