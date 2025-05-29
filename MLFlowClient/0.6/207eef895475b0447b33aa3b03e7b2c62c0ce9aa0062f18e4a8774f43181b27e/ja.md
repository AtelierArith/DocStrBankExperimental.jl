```
setexperimenttag(instance::MLFlow, experiment_id::String, key::String, value::String)
setexperimenttag(instance::MLFlow, experiment_id::Integer, key::String, value::String)
setexperimenttag(instance::MLFlow, experiment::Experiment, key::String, value::String)
```

[`Experiment`](@ref)にタグを設定します。[`Experiment`](@ref)タグは、更新可能なメタデータです。

# 引数

  * `experiment_id`: タグをログする[`Experiment`](@ref)のID。
  * `key`: タグの名前。
  * `value`: ログされるタグの文字列値。

# 戻り値

成功した場合は`true`。そうでない場合は例外を発生させます。
