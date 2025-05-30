```
transitionmodelversionstage(instance::MLFlow, name::String, version::String,
    stage::String, archive_existing_versions::Bool)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` [`RegisteredModel`](@ref) の名前。
  * `version:` [`ModelVersion`](@ref) 番号。
  * `stage:` 新しいステージに移行する [`ModelVersion`](@ref)。
  * `archive_existing_versions:` モデルバージョンを特定のステージに移行する際、このフラグはそのステージにあるすべての既存のモデルバージョンを原子的に「アーカイブ」ステージに移動するかどうかを決定します。これにより、ターゲットステージに存在するモデルバージョンは最大で1つになります。

# 戻り値

更新された [`ModelVersion`](@ref)。
