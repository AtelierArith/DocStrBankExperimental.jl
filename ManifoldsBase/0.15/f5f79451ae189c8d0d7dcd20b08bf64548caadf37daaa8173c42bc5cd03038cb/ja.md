```
submanifold_component(M::AbstractManifold, p, i::Integer)
submanifold_component(M::AbstractManifold, p, ::Val{i}) where {i}
submanifold_component(p, i::Integer)
submanifold_component(p, ::Val{i}) where {i}
```

配列 `p` を `M` に投影してその `i` 番目の成分を取得します。新しい配列が返されます。
