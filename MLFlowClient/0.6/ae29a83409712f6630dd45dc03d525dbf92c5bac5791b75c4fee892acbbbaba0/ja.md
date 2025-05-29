```
getexperimentpermission(instance::MLFlow, experiment_id::String, username::String)
getexperimentpermission(instance::MLFlow, experiment_id::Integer, username::String)
getexperimentpermission(instance::MLFlow, experiment::Experiment, username::String)
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `experiment_id`: [`Experiment`](@ref) ID。
  * `username`: [`User`](@ref) ユーザー名。

# 戻り値

タイプ [`ExperimentPermission`](@ref) のインスタンス。
