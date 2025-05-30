```julia
reset_notebook_environment(notebook_path::String; keep_project::Bool=false, backup::Bool=true)
```

ノートブックファイルから埋め込まれた `Project.toml` と `Manifest.toml` を削除し、ノートブックファイルを修正します。`keep_project` が true の場合、`Manifest.toml` のみが削除されます。ノートブックファイルのバックアップはデフォルトで作成されます。
