```
function assign_boundary_buses!(
    data::Dict{String,<:Any};
    multinetwork::Bool=false
)
```

境界リンクデータに与えられた名前を、対応する送電および配電ネットワークの番号バスに割り当てます。`data`は境界情報を含むpmitd辞書であり、`multinetwork`は割り当てるべき多ネットワーク境界バスがあるかどうかを定義するブール値です。
