```
RunInfo
```

単一の実行のメタデータ。

# フィールド

  * `run_id::String`: 実行の一意の識別子。
  * `run_name::String`: 実行の名前。
  * `experiment_id::String`: 実験ID。
  * `status::RunStatus`: 実行の現在のステータス。
  * `start_time::Int64`: 実行が開始されたときのUnixタイムスタンプ（ミリ秒）。
  * `end_time::Int64`: 実行が終了したときのUnixタイムスタンプ（ミリ秒）。
  * `artifact_uri::String`: アーティファクトをアップロードするディレクトリのURI。これは、ローカルパス（“/”で始まる）または、s3://bucket/directoryやdbfs:/my/directoryのような分散ファイルシステム（DFS）パスである可能性があります。設定されていない場合、ローカルの./mlrunsディレクトリが選択されます。
  * `lifecycle_stage::String`: 実験の現在のライフサイクルステージ："active"または"deleted"。
