```
expected_score(model::ItemResponseModel, theta; scoring_function)
expected_score(model::ItemResponseModel, theta, is; scoring_function)
```

[`ItemResponseModel`](@ref) の期待スコアを計算します。

## 引数

  * `model`: [`ItemResponseModel`](@ref)
  * `theta`: 人のパラメータ値
  * `is`: 1つまたは複数のアイテム識別子。`is`が省略された場合、テスト全体の期待スコアが返されます。

## キーワード引数

  * `scoring_function`: すべての可能な応答値 `y` を値 `x` にマッピングする形式の二項関数 `f(y, ctx) = x`。引数 `ctx` には現在のアイテムコンテキストが含まれます。

## 戻り値

`estimation_type(model) == PointEstimate` の場合、`expected_score` は単一のスカラー値を返す必要があります。

`estimation_type(model) == SamplingEstimate` の場合、`expected_score` は引き出されたサンプルの数と同じ長さの値のベクトルを返す必要があります。 ```
