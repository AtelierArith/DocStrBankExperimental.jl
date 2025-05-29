```
function correct_network_data!(
    data::Dict{String,<:Any};
    multinetwork::Bool=false
)
```

pmおよびpmd辞書のデータを修正し、準備します。また、境界リンクデータで与えられたIDを数値バスに割り当てます。`data`は修正されるpmitd辞書であり、`multinetwork`は割り当てるべき多ネットワーク境界バスがあるかどうかを定義するブール値です。
