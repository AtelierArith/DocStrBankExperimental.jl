```
InelasticNeutronScatteringSpectraData{R<:ReciprocalSpace} <: Data
```

非弾性中性子散乱スペクトルのデータ、含まれるもの：

1. `reciprocalspace::R`: 非弾性中性子散乱スペクトルが計算される逆空間
2. `energies::Vector{Float64}`: エネルギーサンプルポイント。
3. `values::Matrix{Float64}`: 非弾性中性子散乱スペクトルの再スケールされた強度。
