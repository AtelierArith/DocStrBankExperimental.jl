```
PolyZonoForward{A<:PolynomialApproximation,N,R} <: ForwardAlgorithm
```

多項式近似に基づく多項式ゾノトープの前方アルゴリズム [Kochdumper0AB23](@citet)。

### フィールド

  * `polynomial_approximation` – 多項式近似のためのメソッド
  * `reduced_order`          – 各層の後に結果が減少されるオーダー
  * `compact`                  – 各層の後に結果を圧縮するための述語

### 注意事項

デフォルトコンストラクタは、以下のデフォルトを持つキーワード引数を取ります：

  * `polynomial_approximation`: `RegressionQuadratic(10)`、すなわち、10サンプルの二次回帰
  * `compact`: `() -> true`、すなわち、各層の後に圧縮

利用可能な多項式近似メソッドについては、`PolynomialApproximation`のサブタイプを参照してください。
