```
deleteexperimentpermission(instance::MLFlow, experiment_id::String, username::String)
deleteexperimentpermission(instance::MLFlow, experiment_id::Integer, username::String)
deleteexperimentpermission(instance::MLFlow, experiment::Experiment, username::String)
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `experiment_id`: [`Experiment`](@ref) ID。
  * `username`: [`User`](@ref) ユーザー名。

# 戻り値

成功した場合は `true`。それ以外の場合は例外を発生させます。
