```
RelErrorShrink(th, t) <: DNFT
```

相対誤差縮小法は、IEEE Transactions on Signal and Information Processing over Networks, Vol 0, No. 0, 2016の論文「Efficient Approximation and Denoising of Graph Signals using the Multiscale Basis Dictionary」で使用されています。

# 属性

  * `th::Wavelets.Threshold.THType`: (デフォルト: `Wavelets.HardTH()`) 閾値のタイプ。
  * `t::AbstractFloat`: (デフォルト: 1.0) 閾値のサイズ。

# 例

```julia
using Wavelets, WaveletsExt

RelErrorShrink()                    # デフォルトの th と t の値を使用
RelErrorShrink(SoftTH())            # デフォルトの t の値を使用
RelErrorShrink(HardTH(), 0.5)       # ユーザー入力の th と t の値を使用
```

**参照:** [`SureShrink`](@ref), [`VisuShrink`](@ref)
