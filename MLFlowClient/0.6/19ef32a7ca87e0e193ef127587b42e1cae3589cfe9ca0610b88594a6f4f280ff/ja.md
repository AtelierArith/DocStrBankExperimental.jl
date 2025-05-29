```
createexperimentpermission(instance::MLFlow, experiment_id::String, username::String,
    permission::Permission)
createexperimentpermission(instance::MLFlow, experiment_id::Integer, username::String,
    permission::Permission)
createexperimentpermission(instance::MLFlow, experiment::Experiment, username::String,
    permission::Permission)
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `experiment_id`: [`Experiment`](@ref) ID。
  * `username`: [`User`](@ref) ユーザー名。
  * `permission`: [`Permission`](@ref) を付与します。

# 戻り値

タイプ [`ExperimentPermission`](@ref) のインスタンス。
