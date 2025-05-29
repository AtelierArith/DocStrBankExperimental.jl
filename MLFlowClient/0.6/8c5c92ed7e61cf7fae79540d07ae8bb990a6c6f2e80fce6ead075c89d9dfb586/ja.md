```
実験
```

# フィールド

  * `experiment_id::Integer`: 実験の一意の識別子。
  * `name::String`: 実験を識別するための人間が読める名前。
  * `artifact_location::String`: 実験のアーティファクトが保存されている場所。
  * `lifecycle_stage::String`: 実験の現在のライフサイクルステージ: “active” または “deleted”。削除された実験はAPIによって返されません。
  * `last_update_time::Int64`: 最後の更新時刻。
  * `creation_time::Int64`: 作成時刻。
  * `tags::Array{Tag}`: 追加のメタデータのキー-バリューのペア。
