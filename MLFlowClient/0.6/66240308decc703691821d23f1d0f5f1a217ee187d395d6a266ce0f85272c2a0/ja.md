```
updateexperiment(instance::MLFlow, experiment_id::String, new_name::String)
updateexperiment(instance::MLFlow, experiment_id::Integer, new_name::String)
updateexperiment(instance::MLFlow, experiment::Experiment, new_name::String)
```

[`Experiment`](@ref) メタデータを更新します。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `experiment_id`: 関連する [`Experiment`](@ref) の ID。
  * `new_name`: 提供された場合、[`Experiment`](@ref) の名前が新しい名前に変更されます。新しい名前は一意でなければなりません。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
