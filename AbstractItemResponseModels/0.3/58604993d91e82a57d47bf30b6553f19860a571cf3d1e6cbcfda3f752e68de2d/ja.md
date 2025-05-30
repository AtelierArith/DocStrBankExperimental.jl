```
iif(model::ItemResponseModel, theta, i)
iif(model::ItemResponseModel, theta, i, y)
```

## 引数

  * `model`: [`ItemResponseModel`](@ref)
  * `theta`: 人のパラメータ値
  * `i`: 一意のアイテム識別子
  * `y`: 応答値

## 戻り値

`estimation_type(model) == PointEstimate` の場合、アイテム情報関数はスカラー値を返す必要があります。

`estimation_type(model) == SamplingEstimate` の場合、アイテム情報関数は引き出されたサンプルの数と同じ長さの値のベクトルを返す必要があります。
