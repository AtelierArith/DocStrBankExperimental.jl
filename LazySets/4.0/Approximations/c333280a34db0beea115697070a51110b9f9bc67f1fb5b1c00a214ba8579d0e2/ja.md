```
overapproximate(X::Intersection{N, <:AbstractZonotope, <:Hyperplane},
                dirs::AbstractDirections) where {N}
```

ゾノトープ集合とハイパープレーンの交差を、与えられた方向を使用して多面体または多胞体で過大評価します。

### 入力

  * `X`    – ゾノトープ集合とハイパープレーンの交差
  * `dirs` – 方向表現のタイプ

### 出力

ゾノトープ集合とハイパープレーンの交差の過大評価。方向が境界を持つ場合、結果は `HPolytope` になります。それ以外の場合、結果は `HPolyhedron` になります。

### アルゴリズム

この関数は [LeGuernic09; Algorithm 8.1](@citet) を実装しています。
