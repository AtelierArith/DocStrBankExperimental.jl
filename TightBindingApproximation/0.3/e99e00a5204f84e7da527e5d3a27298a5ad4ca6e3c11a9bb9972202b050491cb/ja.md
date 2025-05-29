```
DensityOfStatesData <: Data
```

状態密度のデータ、含まれるもの：

1. `energies::Vector{Float64}`: エネルギーサンプルポイント。
2. `values::Matrix{Float64}`: 特定の軌道セットに投影された状態密度。
