```
logbatch(instance::MLFlow, run_id::String; metrics::MLFlowUpsertData{Metric},
    params::MLFlowUpsertData{Param}, tags::MLFlowUpsertData{Tag})
logbatch(instance::MLFlow, run::Run; metrics::Array{Metric},
    params::MLFlowUpsertData{Param}, tags::MLFlowUpsertData{Tag})
```

[`Run`](@ref) のメトリクス、パラメータ、およびタグのバッチをログに記録します。エラーが発生した場合、部分的なデータが書き込まれる可能性があります。

この関数の詳細については、[MLFlow公式ドキュメント](https://mlflow.org/docs/latest/rest-api.html#log-batch)を参照してください。

# 引数

  * `instance`: [`MLFlow`](@ref) の設定。
  * `run_id`: ログを記録する [`Run`](@ref) のID。
  * `metrics`: ログに記録する [`Metric`](@ref) のコレクション。
  * `params`: ログに記録する [`Param`](@ref) のコレクション。
  * `tags`: ログに記録する [`Tag`](@ref) のコレクション。

**注意**: 単一のリクエストには最大1000のメトリクス、合計で最大1000のメトリクス、パラメータ、およびタグを含めることができます。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
