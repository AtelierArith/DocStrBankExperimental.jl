```
searchexperiments(instance::MLFlow; max_results::Int64=20000, page_token::String="",
    filter::String="", order_by::Array{String}=String[],
    view_type::ViewType=ACTIVE_ONLY)
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `max_results`: 希望する実験の最大数。
  * `page_token`: 取得する実験のページを示すトークン。
  * `filter`: [`Experiment`](@ref) 属性およびタグに対するフィルタ式で、実験のサブセットを返すことを可能にします。詳細は[MLFlowのドキュメント](https://mlflow.org/docs/latest/rest-api.html#search-experiments)を参照してください。
  * `order_by`: 検索結果を並べ替えるための列のリストで、[`Experiment`](@ref) 名および id を含むことができ、オプションで「DESC」または「ASC」の注釈を付けることができます。デフォルトは「ASC」です。
  * `view_type`: 返される実験のタイプを指定する修飾子。指定しない場合は、アクティブな実験のみを返します。詳細な値については[`ViewType`](@ref)を参照してください。

# 戻り値

  * [`MLFlow`](@ref) インスタンスで見つかった[`Experiment`](@ref) のベクター。
  * さらに結果がある場合の次のページトークン。
