```
has_euler_characteristic(edges, faces, vertices)
```

多面体がエッジ、面、頂点を考慮してオイラー特性を持っているかどうかを判断します。

# 例

```julia-repl
julia> has_euler_characteristic(6, 4, 4) # テトラヘドロン
true

julia> has_euler_characteristic(12, 7, 6) # テトラヘミヘキサヘドロン
false
```
