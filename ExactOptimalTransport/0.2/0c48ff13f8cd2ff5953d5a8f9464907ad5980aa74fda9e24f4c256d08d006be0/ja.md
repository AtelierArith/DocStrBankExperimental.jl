```
squared2wasserstein(μ, ν; metric=Euclidean(), kwargs...)
```

`μ`と`ν`の間の`metric`に関する2-Wasserstein距離の二乗を計算します。

残りのキーワード引数は[`ot_cost`](@ref)に渡されます。

参照: [`wasserstein`](@ref), [`ot_cost`](@ref)
