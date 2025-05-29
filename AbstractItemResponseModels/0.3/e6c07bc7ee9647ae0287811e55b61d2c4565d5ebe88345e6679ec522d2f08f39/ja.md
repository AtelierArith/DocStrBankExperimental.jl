```
irf(model::ItemResponseModel, theta, i)
irf(model::ItemResponseModel, theta, i, y)
```

[`ItemResponseModel`](@ref)の項目応答関数を評価します。

## 引数

  * `model`: [`ItemResponseModel`](@ref)
  * `theta`: 人のパラメータ値
  * `i`: 一意の項目識別子
  * `y`: 応答値

## 戻り値

`estimation_type(model) == PointEstimate` の場合、項目応答関数はスカラー値を返す必要があります。

`estimation_type(model) == SamplingEstimate` の場合、項目応答関数はサンプルの数と等しい長さの値のベクトルを返す必要があります。
