```
function external_legs(g::FeynmanGraph)
```

FeynmanGraph `g` の外部頂点が実際の脚を持っているかどうかを示すブールインデックスのリスト external_legs (::Vector{Bool}) を返します（true: 実際の脚、false: 偽の脚）。
