```
getmetrichistory(instance::MLFlow, run_id::String, metric_key::String;
    page_token::String="", max_results::Union{Int64, Missing}=missing)
```

指定された [`Metric`](@ref) のすべての値のリストを、特定の [`Run`](@ref) から取得します。

# 引数

  * `instance`: [`MLFlow`](@ref) の設定。
  * `run_id`: [`Run`](@ref) から取得する [`Metric`](@ref) 値の ID。
  * `metric_key`: 取得する [`Metric`](@ref) の名前。
  * `page_token`: 取得する [`Metric`](@ref) 履歴のページを示すトークン。
  * `max_results`: 呼び出しごとに返す [`Run`](@ref) の [`Metric`](@ref) のログインスタンスの最大数。

# 戻り値

  * 指定された [`Run`](@ref) における指定された [`Metric`](@ref) のすべての履歴値のリスト。
  * さらに結果がある場合の次のページトークン。
