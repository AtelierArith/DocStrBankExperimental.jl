```
model = FirstOrderModel(f, ∇f!; name = "first-order model")
```

滑らかな目的関数を表す `AbstractNLPModel` の単純なサブタイプです。

## 引数

  * `f :: F <: Function`: `f(x)` が `x` における目的値を返す関数;
  * `∇f! :: G <: Function`: `∇f!(g, x)` が `x` における目的の勾配を `g` に格納する関数;
  * `x :: AbstractVector`: 初期推定値。

すべてのキーワード引数は `NLPModelMeta` コンストラクタに渡されます。
