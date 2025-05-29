```
ModelVersion
```

# フィールド

  * `name::String`: モデルのユニークな名前。
  * `version::String`: モデルのバージョン番号。
  * `creation_timestamp::Int64`: この model_version が作成されたときに記録されたタイムスタンプ。
  * `last_updated_timestamp::Int64`: この model_version のメタデータが最後に更新されたときに記録されたタイムスタンプ。
  * `user_id::Union{String, Nothing}`: この model_version を作成したユーザー。
  * `current_stage::String`: この model_version の現在のステージ。
  * `description::String`: この model_version の説明。
  * `source::String`: model_version を作成する際に使用されるソースモデルアーティファクトの場所を示す URI。
  * `run_id::String`: model_version を作成する際に使用される MLflow ラン ID。ソースが MLflow トラッキングサーバーに保存された実験ランによって生成された場合。
  * `status::ModelVersionStatus`: model_version の現在のステータス。
  * `status_message::String`: 現在のステータスに関する詳細、保留中または失敗している場合。
  * `tags::Array{Tag}`: 追加のメタデータのキーと値のペア。
  * `run_link::String`: このバージョンを生成したランへの直接リンク。このフィールドは、ソースランがレジストリサーバーとは異なるトラッキングサーバーからのものである model_version の作成時にのみ設定されます。
  * `aliases::Array{String}`: この model_version を指すエイリアス。
