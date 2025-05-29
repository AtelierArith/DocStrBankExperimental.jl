```
locwlv(Xtrain, Ytrain, X; listnn, listw = nothing, algo, nlv, verbose = true, kwargs...)
```

与えられたkNNモデルの予測を計算します。

  * `Xtrain` : トレーニングXデータ。
  * `Ytrain` : トレーニングYデータ。
  * `X` : 予測するXデータ（m観測）。

キーワード引数：

  * `listnn` : m個のインデックスのベクトルのリスト（ベクトル）。
  * `listw` : m個の重みのベクトルのリスト（ベクトル）。
  * `algo` : m個の近傍でモデルを計算する関数。
  * `nlv` : 潜在変数（LV）の数またはコレクション。
  * `verbose` : ブール値。`true`の場合、予測情報が印刷されます。
  * `kwargs` : 関数`algo`に渡すキーワード引数。各引数は長さ=1でなければならず（コレクションであってはならない）。

[`locw`](@ref)と同じですが、LVベースのモデル（例：PLSR）に特化しており、はるかに高速です。
