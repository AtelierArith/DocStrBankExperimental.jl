```
ρ(d::AbstractVector, cap::Intersection{N, S1, S2}; kwargs...
 ) where {N, S1<:AbstractPolyhedron, S2<:AbstractPolyhedron}
```

二つの多面体集合の交差の支持関数を評価します。

### 入力

  * `d`      – 方向
  * `cap`    – 二つの多面体集合の交差
  * `kwargs` – 支持関数アルゴリズムに渡される追加の引数

### 出力

指定された方向における支持関数の評価。

### アルゴリズム

二つの多面体の制約を新しい `HPolyhedron` に結合し、その後支持関数を評価します。
