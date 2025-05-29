```
overapproximate(P::SparsePolynomialZonotope{N}, ::Type{<:VPolytope}) where {N}
```

スパース多項式ゾノトープを頂点表現のポリトープで過大評価します。

### 入力

  * `P`         – スパース多項式ゾノトープ
  * `VPolytope` – 目標タイプ

### 出力

`VPolytope`。

### アルゴリズム

このメソッドは[Kochdumper21a; Proposition 3.1.15](@citet)を実装しています。アイデアは、`P`を線形部分と非線形部分に分割することです（`P = P₁ ⊕ P₂`となるように）。非線形部分はゾノトープで囲まれます。次に、両方の集合の頂点を組み合わせ、最後に凸包アルゴリズムを適用します。
