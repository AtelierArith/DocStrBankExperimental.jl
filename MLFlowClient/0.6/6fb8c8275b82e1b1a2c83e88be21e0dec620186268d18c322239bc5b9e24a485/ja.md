```
ユーザー
```

# フィールド

  * `id::String`: ユーザーID。
  * `username::String`: ユーザー名。
  * `is_admin::Bool`: ユーザーが管理者かどうか。
  * `experiment_permissions::Array{ExperimentPermission}`: ユーザーに明示的に付与されたすべての実験権限。
  * `registered_model_permissions::Array{RegisteredModelPermission}`: ユーザーに明示的に付与されたすべての登録モデル権限。
