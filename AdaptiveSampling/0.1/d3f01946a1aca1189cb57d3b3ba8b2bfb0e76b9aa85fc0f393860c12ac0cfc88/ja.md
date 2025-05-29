```
VisvalingamCost <: AbstractCost{3}
```

2点間のVisvalingam-Whyatt面積ベースのコストを計算するコスト関数です。コストは、指定されたノルムで正規化された点によって形成される面積の平方根として定義されます：

$$
cost(x, y) = \sqrt{\frac{\text{area}(x, y)}{\text{norm}}}
$$

ここで、`area(x, y)`は、`x`と`y`の点によって形成される三角形の面積であり、各点は`x`-`y`平面の3つの点を識別する長さ3を持ちます。

# フィールド

  * `norm::Float64`: コストの正規化因子。

# コンストラクタ

  * `VisvalingamCost()`: デフォルトのノルム`1.0`で`VisvalingamCost`を作成します。
  * `VisvalingamCost(norm)`: 指定されたノルムで`VisvalingamCost`を作成します。
  * `VisvalingamCost(a, b, fa, fb)`: 点`(a, fa)`と`(b, fb)`によって形成される三角形の面積をノルムに設定した`VisvalingamCost`を作成します。
