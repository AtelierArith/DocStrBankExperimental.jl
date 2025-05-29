```
adjr2(model::StatisticalModel, variant::Symbol)
adjr²(model::StatisticalModel, variant::Symbol)
```

調整済み擬似決定係数（調整済み擬似R二乗）。非線形モデルの場合、いくつかの擬似R²定義の中から`variant`を介して選択する必要があります。現在サポートされている唯一のバリアントは`:MacFadden`で、これは$1 - (\log (L) - k)/\log (L0)$として定義され、`:devianceratio`は$1 - (D/(n-k))/(D_0/(n-1))$として定義されます。これらの式において、$L$はモデルの尤度、$L0$はヌルモデル（切片のみを含むモデル）の尤度、$D$はモデルの偏差、$D_0$はヌルモデルの偏差、$n$は観測数（[`nobs`](@ref)によって与えられる）であり、$k$はモデルの消費された自由度の数（[`dof`](@ref)によって返される）です。
