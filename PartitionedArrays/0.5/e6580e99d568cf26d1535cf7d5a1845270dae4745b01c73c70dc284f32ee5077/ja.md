```
replace_ghost(indices,gids,owners)
```

`indices`内のゴーストインデックスを`gids`内のグローバルIDおよび`owners`内のオーナーで置き換えます。返されるオブジェクトは`gids`と`owners`の所有権を持ちます。このメソッドは、`indices`が[`OwnAndGhostIndices`](@ref)のようにゴーストIDを別のベクターに格納している場合にのみ意味があります。`gids`は一意であり、`indices`によって所有されていない必要があります。
