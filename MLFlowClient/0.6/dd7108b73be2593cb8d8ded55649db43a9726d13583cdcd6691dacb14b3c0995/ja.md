```
RegisteredModel
```

# フィールド

  * `name::String`: モデルのユニークな名前。
  * `creation_timestamp::Int64`: この RegisteredModel が作成されたときに記録されたタイムスタンプ。
  * `last_updated_timestamp::Int64`: この RegisteredModel のメタデータが最後に更新されたときに記録されたタイムスタンプ。
  * `user_id::Union{String, Nothing}`: この RegisteredModel を作成したユーザー。
  * `description::Union{String, Nothing}`: この RegisteredModel の説明。
  * `latest_versions::Array{ModelVersion}`: 各ステージの最新モデルバージョンのコレクション。現在の READY ステータスのモデルのみを含む。
  * `tags::Array{Tag}`: 追加のメタデータのキーと値のペア。
  * `aliases::Array{RegisteredModelAlias}`: この RegisteredModel に関連付けられたモデルバージョンを指すエイリアス。
