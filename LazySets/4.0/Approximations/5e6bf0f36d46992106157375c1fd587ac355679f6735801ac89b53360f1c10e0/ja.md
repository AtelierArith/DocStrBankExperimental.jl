```
overapproximate(r::Rectification{N, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

ゾノトピック集合の整形の上限近似をゾノトープで行います。

### 入力

  * `r`        – ゾノトピック集合の遅延整形
  * `Zonotope` – 目標集合タイプ

### 出力

整形された `Z` によって得られた集合のゾノトープの上限近似。

### アルゴリズム

このメソッドは [SinghGMPV18; Theorem 3.1](@citet) を実装しています。
