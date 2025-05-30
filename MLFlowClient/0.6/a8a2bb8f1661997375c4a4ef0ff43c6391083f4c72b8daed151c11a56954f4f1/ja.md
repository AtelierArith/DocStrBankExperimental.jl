```
searchruns(instance::MLFlow; experiment_ids::Array{String}=String[], filter::String="",
    run_view_type::ViewType=ACTIVE_ONLY, max_results::Int=1000,
    order_by::Array{String}=String[], page_token::String="")
```

実行を満たす式を検索します。検索式は[`Metric`](@ref)および[`Param`](@ref)キーを使用できます。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `experiment_ids`: 検索対象の[`Experiment`](@ref) IDのリスト。
  * `filter`: パラメータ、メトリクス、およびタグに対するフィルタ式で、実行のサブセットを返すことを可能にします。詳細は[MLFlowのドキュメント](https://mlflow.org/docs/latest/rest-api.html#search-runs)を参照してください。
  * `run_view_type`: アクティブな実行のみ、削除された実行のみ、またはすべての実行を表示するかどうか。デフォルトはアクティブな実行のみです。
  * `max_results`: 希望する最大実行数。
  * `order_by`: 属性、パラメータ、メトリクス、およびタグを含む、順序付ける列のリストで、オプションの「DESC」または「ASC」注釈を付けることができ、「ASC」がデフォルトです。
  * `page_token`: 取得する実行のページを示すトークン。

# 戻り値

  * 指定された実験で見つかった[`Run`](@ref)のベクター。
  * さらに結果がある場合の次のページトークン。
