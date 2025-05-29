```
SuperAncSaturation <: SaturationMethod
SuperAncSaturation()
```

`saturation_pressure`のための飽和法です。これは、拡張精度算術を用いて構築されたチェビシェフ展開を使用して、`Float64`精度内のサポートされているEoSの飽和曲線を取得します。サポートされているモデルは次のとおりです：

  * [vdW](@ref) モデルとそのバリエーション
  * [RK](@ref) モデルとそのバリエーション
  * [PR](@ref) モデルとそのバリエーション
  * [PCSAFT](@ref) モデルといくつかのバリエーション（`EoSSuperancillaries.jl`パッケージ拡張を介して）

## 参考文献

1. Bell, I. H., & Deiters, U. K. (2021). Superancillary equations for cubic equations of state. Industrial & Engineering Chemistry Research, 60(27), 9983–9991. doi:10.1021/acs.iecr.1c00847
