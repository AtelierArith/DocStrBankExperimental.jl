```
deleteexperiment(instance::MLFlow, experiment_id::String)
deleteexperiment(instance::MLFlow, experiment_id::Integer)
deleteexperiment(instance::MLFlow, experiment::Experiment)
```

[`Experiment`](@ref) と関連するメタデータ、ラン、メトリクス、パラメータ、およびタグを削除のためにマークします。[`Experiment`](@ref) が FileStore を使用している場合、[`Experiment`](@ref) に関連するアーティファクトも削除されます。

# 引数

  * `instance`: [`MLFlow`](@ref) の設定。
  * `experiment_id`: 関連する [`Experiment`](@ref) の ID。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
