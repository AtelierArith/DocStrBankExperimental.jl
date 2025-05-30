```
createregisteredmodel(instance::MLFlow, name::String;
    tags::MLFlowUpsertData{Tag}=Tag[], description::Union{String, Missing}=missing)
```

名前を持つ [`RegisteredModel`](@ref) を作成します。新しく作成された [`RegisteredModel`](@ref) を返します。同じ名前の別の [`RegisteredModel`](@ref) が既に存在しないことを検証し、同じ名前の別の [`RegisteredModel`](@ref) が既に存在する場合は失敗します。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `name`: この名前の下でモデルを登録します。
  * `tags`: [`Tag`](@ref) のコレクション。
  * `description`: [`RegisteredModel`](@ref) のオプションの説明。

# 返り値

タイプ [`RegisteredModel`](@ref) のインスタンス。
