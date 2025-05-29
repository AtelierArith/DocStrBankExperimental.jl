```
EuclideanCost <: AbstractCost{2}
```

入力ベクトルの最初と最後の要素間のユークリッド距離としてコストを計算し、指定されたノルムで正規化するコスト関数：

$$
cost(x, y) = \frac{\sqrt{(x[end] - x[1])^2 + (y[end] - y[1])^2}}{\text{norm}}
$$

# フィールド

  * `norm::Float64`: コストの正規化因子。

# コンストラクタ

  * `EuclideanCost()`: デフォルトのノルム `1.0` で `EuclideanCost` を作成します。
  * `EuclideanCost(norm)`: 指定されたノルムで `EuclideanCost` を作成します。
  * `EuclideanCost(a, b, fa, fb)`: 点 `(a, fa)` と `(b, fb)` の間のユークリッド距離をノルムとして設定した `EuclideanCost` を作成します。
