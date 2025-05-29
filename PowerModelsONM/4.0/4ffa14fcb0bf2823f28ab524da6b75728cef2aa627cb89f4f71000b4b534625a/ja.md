```
get_timestep_generator_profiles(
    solution::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

最適な dispatch `solution` からの発電機プロファイルに関する統計を返します：

  * `"Grid mix (kW)"`: 変電所からの電力
  * `"Solar DG (kW)"`: 太陽光 PV DER からの電力
  * `"Energy storage (kW)"`: エネルギー貯蔵 DER からの電力
  * `"Diesel DG (kW)"`: 従来の発電機 DER からの電力
