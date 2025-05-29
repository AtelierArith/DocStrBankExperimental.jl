```
grow_dst!(dst::AbstractVector{UInt8}, max_size::Int64)::Union{Nothing, Int64}
```

宛先ベクター `dst` を現在のサイズと `max_size` の間のサイズに成長させます。 `dst` が成長した場合は新しいサイズを返し、`max_size` 制限のために成長できなかった場合は `nothing` を返します。
