```
SureShrink(th, t) <: DNFT
```

スタインのバイアスのないリスク推定（SURE）シュリンク

# 属性

  * `th::Wavelets.Threshold.THType`: (デフォルト: `Wavelets.HardTH()`) 閾値の種類。
  * `t::AbstractFloat`: (デフォルト: 1.0) 閾値のサイズ。

**参照:** [`RelErrorShrink`](@ref), [`VisuShrink`](@ref)
