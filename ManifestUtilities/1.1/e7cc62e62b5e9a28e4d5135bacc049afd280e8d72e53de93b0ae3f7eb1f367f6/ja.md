```
prune_manifest(; kwargs...) --> new_manifest::AbstractString
```

与えられたプロジェクトとマニフェストを解析し、指定されたプロジェクトの直接的または間接的（再帰的）依存関係のみを含む新しいマニフェストを生成します。新しいマニフェストは `AbstractString` として返されます。

## 必要なキーワード引数

`project` と `project_filename` のいずれか一方（正確に一つ）を指定する必要があります。同様に、`manifest` と `manifest_filename` のいずれか一方（正確に一つ）を指定する必要があります。

  * `project::Union{AbstractString, IO}`: 入力 `Project.toml` ファイルの内容
  * `project_filename::AbstractString`: 入力 `Project.toml` ファイルのファイル名
  * `manifest::Union{AbstractString, IO}`: 入力 `Manifest.toml` ファイルの内容
  * `manifest_filename::AbstractString`: 入力 `Manifest.toml` ファイルのファイル名
