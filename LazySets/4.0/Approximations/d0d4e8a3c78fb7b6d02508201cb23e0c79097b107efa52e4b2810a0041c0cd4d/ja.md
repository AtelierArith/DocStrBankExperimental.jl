```
overapproximate(X::Intersection{N, <:AbstractZonotope, <:Hyperplane},
                ::Type{<:Zonotope})
```

ゾノトピック集合とハイパープレーンの交差をゾノトープで過大評価します。

### 入力

  * `X`        – ゾノトピック集合とハイパープレーンの交差
  * `Zonotope` – 目標集合タイプ

### 出力

交差を過大評価するゾノトープ。

### アルゴリズム

このメソッドは [MaigaRTC14; Algorithm 3](@citet) を実装しています。
