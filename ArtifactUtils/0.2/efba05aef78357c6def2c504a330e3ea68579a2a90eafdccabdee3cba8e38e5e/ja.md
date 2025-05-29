```
upload_all_to_gist!(
    artifacts_toml::AbstractString;
    extension::AbstractString = ".tar.gz",
    private::Bool = true,
    append::Bool = false,
)
```

`artifacts_toml`内のすべてのアーティファクトエントリを`.download.url`プロパティなしでアップロードし（デフォルト）、その後`artifacts_toml`を更新します。

# キーワード引数

  * `extension`: アーティファクトアーカイブファイルのファイル拡張子
  * `private`: `true`の場合、アーカイブをプライベートギストにアップロード
  * `append`: `true`の場合、`download`エントリが存在してもアーカイブをアップロード
