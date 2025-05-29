```
lead(panel::PanelStructure, v::AbstractArray, l::Integer=1; default=missing)
```

ベクトル `v` の `l` 番目のリード値を返し、欠損値は `default` で埋められます。`panel` 構造は尊重されます。詳細は [`ilead!`](@ref) と [`lag`](@ref) を参照してください。
