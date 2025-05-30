```
refresh(instance::MLFlow, run::Run)
refresh(instance::MLFlow, experiment::Experiment)
```

最新のメタデータを[`Run`](@ref)または[`Experiment`](@ref)のために取得します。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `run`または`experiment`: 更新する[`Run`](@ref)または[`Experiment`](@ref)。

# 戻り値

[`Run`](@ref)または[`Experiment`](@ref)のインスタンス。
