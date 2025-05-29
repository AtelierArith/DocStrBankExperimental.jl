```
get_timestep_storage_soc(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Vector{Real}
```

ストレージの充電状態、すなわち最適なディスパッチ `solution` に基づいてすべてのエネルギー貯蔵DERに残っているエネルギーの量を返します。パーセンテージを提供するために `network` が必要です。
