```
krull_dim(R::Ring)
```

リング $R$ のクルル次元を返します。このメソッドは現在、特定の可換ノーザリアン環にのみ対応しています。

# 例

```jldoctest
julia> R, x = polynomial_ring(ZZ, [:x]);

julia> krull_dim(R)
2
```
