`QuadGK`モジュールは、適応ガウス–クロンロッドアルゴリズムによる1次元数値積分を実装しています。

このパッケージは、`quadgk`、`gauss`、および`kronrod`の3つの関数を提供します。

  * `quadgk`は任意の区間にわたる適応積分を実行します
  * `gauss`は区間[-1, 1]にわたる積分のためのガウス求積点と重みを計算します
  * `kronrod`は[-1, 1]にわたる積分のためのクロンロッド点、重み、および埋め込まれたガウス求積重みを計算します。

典型的な使用法は次のようになります：

```julia
using QuadGK
integral, err = quadgk(x -> exp(-x^2), 0, 1, rtol=1e-8)
```

これは、x=0からx=1までのexp(–x²)の積分を相対許容誤差10⁻⁸で計算し、近似値`integral = 0.746824132812427`と誤差推定`err = 7.887024366937112e-13`を返します。
