```
thermal_SZ( n_cm3::Vector{<:Real}, T_K::Vector{<:Real},
            z::Real=0.0, ν::Real=1.44e9; 
            DI_over_I::Bool=false )
```

電子密度 `n_cm3` と赤外線 `T_K` の温度を用いて、赤方偏移 `z` と観測周波数 `ν` における熱的スニャエフ・ゼルドビッチ効果を計算します。`DI_over_I` を `true` に設定すると単位が $dI/I$ で出力され、それ以外の場合は `dT/T` になります。

## 引数:

  * `n_cm3`: SPH 粒子密度 [1/cm^3]
  * `T_K`: SPH 粒子温度 [K]
  * `z`: 赤方偏移
  * `ν`: 観測周波数

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`

```
