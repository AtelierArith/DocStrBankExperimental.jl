```
UniformCost <: AbstractCost{2}
```

入力ベクトルの最初と最後の要素の絶対差を計算し、指定されたノルムで正規化するコスト関数：

$$
cost(x, y) = \frac{|x[end] - x[1]|}{\text{norm}}
$$

# フィールド

  * `norm::Float64`: コストの正規化因子。

# コンストラクタ

  * `UniformCost()`: デフォルトのノルム `1.0` で `UniformCost` を作成します。
  * `UniformCost(norm)`: 指定されたノルムで `UniformCost` を作成します。
  * `UniformCost(a, b)`: `a` と `b` の絶対差をノルムとして設定した `UniformCost` を作成します。
