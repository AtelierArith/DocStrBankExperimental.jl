```
weight(::Type{<:WeightNormalization}, cxr::CharXRay)
```

ここで `WeightNormalization` は次のいずれかです：

  * `NormalizeByShell` は、シェルに関連付けられたすべての重みの合計を1に正規化します。
  * `NormalizeBySubShell` は、各サブシェルに関連付けられたすべての重みの合計を1に正規化します。
  * `NormalizeToUnity` は、各シェルの中で最も強い線を1.0にするように強度を正規化します。

`cxr` の相対的な強度をそのシェル、サブシェルなどの他の特性X線に対して粗い推定を計算します。異なる `WeightNormalization` モードは、`weight(...)` 関数が使用される異なる方法を反映しています。

`fluorescenceyield(...)` と `weight(...)` の違いは次のとおりです：

  * fluorescenceyield は、原子のサブシェルがすでにイオン化されていると仮定します。
  * weight は、過電圧4.0を仮定して各サブシェルのイオン化の相対的な可能性も考慮します。
