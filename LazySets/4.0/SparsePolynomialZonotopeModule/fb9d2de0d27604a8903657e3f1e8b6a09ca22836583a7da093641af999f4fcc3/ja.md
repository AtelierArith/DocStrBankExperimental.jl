```
ρ(d::AbstractVector, P::SparsePolynomialZonotope; [enclosure_method]=nothing)
```

$$
P
$$

のサポート関数を方向$d$で制約します。

### 入力

  * `d`                – 方向
  * `P`                – スパース多項式ゾノトープ
  * `enclosure_method` – （オプション; デフォルト: `nothing`）制約に使用する方法; [`Rangeenclosures.jl`](https://github.com/JuliaReach/RangeEnclosures.jl) パッケージの `AbstractEnclosureAlgorithm`

### 出力

指定された方向におけるサポート関数の過大評価。

### アルゴリズム

このメソッドは [Kochdumper21a; Proposition 3.1.16](@citet) を実装しています。
