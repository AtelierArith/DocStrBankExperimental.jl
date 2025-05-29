```
kinetic_SZ(n_cm3::Real, vel_y_cgs::Real, 
           z::Real=0.0, ν::Real=1.e9;
           DI_over_I::Bool=false)
```

電子密度 `n_cm3` と cgs 単位での投影面に対する y 方向の速度 `vel_y_cgs` から運動的 Sunyaev-Zel'dovich 効果を計算します。`DI_over_I` が `true` に設定されている場合は、観測周波数 `ν` と赤方偏移 `z` も提供する必要があります。

## 引数:

  * `n_cm3`: SPH 粒子密度 [1/cm^3]
  * `vel_y_cgs`: SPH 粒子の y 方向の速度 [cm/s]
  * `z`: 赤方偏移
  * `ν`: 観測周波数

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`

```
