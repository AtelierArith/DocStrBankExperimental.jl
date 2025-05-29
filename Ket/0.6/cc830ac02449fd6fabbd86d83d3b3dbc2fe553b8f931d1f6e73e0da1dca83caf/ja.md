```
channel_amplitude_damping_generalized(rho::AbstractMatrix, p::Real, γ::Real)
```

一般化振幅減衰チャネルのクローズ演算子表現を返します。これは、有限温度の環境への散逸の影響を説明します。`γ`は、系が基底状態に崩壊する確率です。`1-p`は定常状態のエネルギーと考えることができます。
