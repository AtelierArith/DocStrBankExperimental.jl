```
model = FirstOrderNLSModel(r!, jv!, jtv!; name = "first-order NLS model")
```

滑らかな残差を持つ非線形最小二乗問題を表す `AbstractNLSModel` の単純なサブタイプです。

## 引数

  * `r! :: R <: Function`: `r!(y, x)` が `x` における残差を `y` に格納する関数;
  * `jv! :: J <: Function`: `jv!(u, x, v)` が `x` における残差ヤコビアンとベクトル `v` の積を `u` に格納する関数;
  * `jtv! :: Jt <: Function`: `jtv!(u, x, v)` が `x` における残差ヤコビアンの転置とベクトル `v` の積を `u` に格納する関数;
  * `x :: AbstractVector`: 初期推定値。

すべてのキーワード引数は `NLPModelMeta` コンストラクタに渡されます。
