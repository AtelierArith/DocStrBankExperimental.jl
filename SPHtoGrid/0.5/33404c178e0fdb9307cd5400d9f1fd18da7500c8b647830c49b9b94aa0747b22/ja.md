```
comptonY(n_cm3::Real, T_K::Real, z::Real)
```

電子密度 `n_cm3` と温度 `T`（ケルビン）を用いて、赤方偏移 `z` におけるコンプトン-Yパラメータを計算します。

## 引数:

  * `n_cm3`: SPH粒子密度 [1/cm^3]
  * `T_K`: SPH粒子温度 [K]
  * `z`: 赤方偏移。

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`
