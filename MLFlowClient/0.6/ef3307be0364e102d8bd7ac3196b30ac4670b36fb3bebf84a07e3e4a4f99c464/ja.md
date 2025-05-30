```
getexperiment(instance::MLFlow, experiment_id::String)
getexperiment(instance::MLFlow, experiment_id::Integer)
```

[`Experiment`](@ref)のメタデータを取得します。このメソッドは削除された実験でも機能します。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `experiment_id`: 関連する[`Experiment`](@ref)のID。

# 戻り値

[`Experiment`](@ref)型のインスタンス。
