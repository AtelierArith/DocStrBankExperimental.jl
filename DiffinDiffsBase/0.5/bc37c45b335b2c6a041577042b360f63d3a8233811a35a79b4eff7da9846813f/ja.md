```
lag(panel::PanelStructure, v::AbstractArray, l::Integer=1; default=missing)
```

`v`の`l`番目の遅延値のベクトルを返し、欠損値は`default`で埋められます。`panel`構造は尊重されます。[`ilag!`](@ref)および[`lead`](@ref)も参照してください。
