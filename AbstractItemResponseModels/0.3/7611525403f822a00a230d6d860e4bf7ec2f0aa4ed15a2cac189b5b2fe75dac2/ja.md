```
information(model::ItemResponseModel, theta; scoring_function)
information(model::ItemResponseModel, theta, is; scoring_function)
```

[`ItemResponseModel`](@ref) の情報を計算します。

## 引数

  * `theta`: 人のパラメータ値
  * `is`: 1つまたは複数のアイテム識別子。`is` が省略された場合、テスト全体の情報（テスト情報）が返されます。

## キーワード引数

  * `scoring_function`: すべての可能な応答値 `y` を値 `x` にマッピングする形式の2項関数 `f(y, ctx) = x`。引数 `ctx` には現在のアイテムコンテキストが含まれます。

## 戻り値

もし `estimatione_type(model) == PointEstimate` ならば、`information` は単一のスカラー値を返さなければなりません。

もし `estimation_type(model) == SamplingEstimate` ならば、`information` は引かれたサンプルの数と等しい長さの値のベクトルを返さなければなりません。
