```
createexperiment(instance::MLFlow, name::String;
    artifact_location::Union{String, Missing}=missing,
    tags::MLFlowUpsertData{Tag}=Tag[])
```

名前を持つ[`Experiment`](@ref)を作成します。新しく作成された[`Experiment`](@ref)を返します。同じ名前の別の[`Experiment`](@ref)が既に存在しないことを検証し、同じ名前の[`Experiment`](@ref)が既に存在する場合は失敗します。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `name`: [`Experiment`](@ref)の名前。このフィールドは必須です。
  * `artifact_location`: [`Experiment`](@ref)のすべてのアーティファクトが保存される場所。指定しない場合、リモートサーバーが適切なデフォルトを選択します。
  * `tags`: [`Experiment`](@ref)に設定する[`Tag`](@ref)のコレクション。

# 戻り値

新しく作成された[`Experiment`](@ref)のID。
