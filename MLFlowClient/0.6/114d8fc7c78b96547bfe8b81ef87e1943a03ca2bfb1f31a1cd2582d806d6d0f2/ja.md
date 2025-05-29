```
restoreexperiment(instance::MLFlow, experiment_id::String)
restoreexperiment(instance::MLFlow, experiment_id::Integer)
restoreexperiment(instance::MLFlow, experiment::Experiment)
```

削除のためにマークされた[`Experiment`](@ref)を復元します。これにより、関連するメタデータ、実行、メトリクス、パラメータ、およびタグも復元されます。[`Experiment`](@ref)がFileStoreを使用している場合、[`Experiment`](@ref)に関連する基礎となるアーティファクトも復元されます。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `experiment_id`: 関連する[`Experiment`](@ref)のID。

# 戻り値

成功した場合は`true`を返します。それ以外の場合は例外を発生させます。
