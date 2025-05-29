```
struct BoggsChargeTrappingModel{T <: SSDFloat} <: AbstractChargeTrappingModel{T}
```

ボッグスらによって提示されたチャージトラッピングモデル [Boggs *et al.* (2023)](https://doi.org/10.1016/j.nima.2023.168756)。

## フィールド

  * `nσe::T`: 電子のトラッピング生成物 (デフォルト: `(nσe)^-1 = 1020cm`)。
  * `nσh::T`: ホールのトラッピング生成物 (デフォルト: `(nσh)^-1 = 2040cm`)。
  * `temperature::T`: 結晶の温度 (デフォルト: `78K`)。

詳細は [Charge Trapping Models](@ref) を参照してください。
