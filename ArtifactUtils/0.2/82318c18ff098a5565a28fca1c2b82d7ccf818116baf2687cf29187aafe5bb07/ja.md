```
upload_to_gist(
    artifact_id::SHA1,
    [tarball];
    private::Bool = true,
    honor_overrides = false,
    # 以下のオプションは `tarball` が指定されていない場合にのみ利用可能です:
    name::AbstractString = "$artifact_id.tar.gz",
    extension::AbstractString = ".tar.gz",
) -> gist
```

パス `tarball` にアーティファクトアーカイブを作成し（または一時的な場所に）、それをgistにアップロードします。返される値 `gist` は `add_artifact!` に渡すことができます。

# 拡張ヘルプ

## 例

```julia
using ArtifactUtils
add_artifact!("Artifact.toml", "name", upload_to_gist(artifact_from_directory("source")))
```

`"source"` ディレクトリ内のファイルからアーティファクトを作成し、それをgistにアップロードし、次に `"name"` という名前で `"Artifact.toml"` に追加します。

## キーワード引数

  * `private`: `true` の場合、アーカイブをプライベートgistにアップロードします
  * `name`: アーカイブファイルの名前（ファイル拡張子を含む）
  * `extension`: tarballのファイル拡張子。圧縮方法を指定するために使用できます。
  * `honor_overrides`: `Pkg.Artifacts.archive_artifact` を参照してください
