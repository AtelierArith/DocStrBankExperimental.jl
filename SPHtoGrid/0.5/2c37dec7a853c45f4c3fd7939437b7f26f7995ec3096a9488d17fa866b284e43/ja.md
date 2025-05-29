```
comptonY(n_cm3::Vector{<:Real}, T_K::Vector{<:Real}, z::Real)
```

電子密度 `n_cm3` と赤色移動 `z` におけるケルビン温度 `T` からコンプトン-Yパラメータを計算します。

## 引数:

  * `n_cm3`: SPH粒子密度 [1/cm^3]
  * `T_K`: SPH粒子温度 [K]
  * `z`: 赤色移動

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`
