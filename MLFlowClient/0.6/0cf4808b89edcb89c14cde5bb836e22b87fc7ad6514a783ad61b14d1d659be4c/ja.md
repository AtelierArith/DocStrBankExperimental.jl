```
searchregisteredmodels(instance::MLFlow, filter::String, max_results::Int64,
    order_by::String, page_token::String)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `filter`: 文字列フィルター条件。詳細は [MLFlow ドキュメント](https://mlflow.org/docs/latest/rest-api.html#search-registeredmodels) を参照してください。
  * `max_results`: 希望するモデルの最大数。
  * `order_by`: 検索結果を並べ替えるための列のリスト。モデル名や最終更新タイムスタンプを含むことができ、オプションで「DESC」または「ASC」の注釈を付けることができます。「ASC」がデフォルトです。同点の場合はモデル名のASCで決定されます。
  * `page_token`: 前の検索クエリに基づいて次のページに移動するためのページネーショントークン。

# 戻り値

  * [`MLFlow`](@ref) インスタンスで見つかった [`RegisteredModel`](@ref) のベクター。
  * さらに結果がある場合の次のページトークン。
