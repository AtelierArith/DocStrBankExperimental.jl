```
unflatten(T::Type, data, use::Type=Real)
```

型 `T` とタプルまたはベクター `data` からオブジェクトを構築します。`data` は `T` のクエリされたフィールド（型 `use`）と同じかそれ以上の長さである必要があります。

# 例

```julia
julia> unflatten(Tuple{Tuple{Int,Int},Complex{Int,Int}}, (1, 2, 3, 4))
((1, 2), 3 + 4im)

```
