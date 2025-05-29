```
deviance(m::GeneralizedLinearMixedModel{T}, nAGQ=1)::T where {T}
```

`m`の偏差をラプラス近似（`nAGQ=1`）または`nAGQ`点適応ガウス-エルミート数値積分によって評価します。

分布`D`にスケールパラメータがない場合、ラプラス近似は条件付きモードの二乗長さ$u$、および$\det(Λ'Z'WZΛ + I)$、さらに二乗偏差残差の合計を加えたものです。
