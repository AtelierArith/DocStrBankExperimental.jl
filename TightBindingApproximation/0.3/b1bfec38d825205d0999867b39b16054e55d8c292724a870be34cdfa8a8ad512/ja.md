```
EnergyBandsData{R<:ReciprocalSpace, W<:Union{Array{Float64, 3}, Nothing}} <: Data
```

エネルギーバンドのデータ、含まれるもの：

1. `reciprocalspace::R`: エネルギーバンドが計算される逆空間。
2. `values::Matrix{Float64}`: 各列が同じ逆点での値を格納するバンドの固有エネルギー。
3. `weights::W`: `nothing`でない場合、エネルギーバンドに投影された特定の軌道のセットの重み。
