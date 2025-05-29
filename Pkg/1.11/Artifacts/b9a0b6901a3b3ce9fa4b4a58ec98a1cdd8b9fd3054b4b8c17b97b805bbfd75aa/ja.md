```
bind_artifact!(artifacts_toml::String, name::String, hash::SHA1;
               platform::Union{AbstractPlatform,Nothing} = nothing,
               download_info::Union{Vector{Tuple},Nothing} = nothing,
               lazy::Bool = false,
               force::Bool = false)
```

指定された `(Julia)Artifacts.toml` ファイル内に `name` -> `hash` のマッピングを書き込みます。`platform` が `nothing` でない場合、このアーティファクトはプラットフォーム固有としてマークされ、マルチマッピングになります。同じ `artifacts_toml` 内で異なる `platform` と `hash` を持つ同じ名前の複数のアーティファクトをバインドすることは有効です。`force` が `true` に設定されている場合、既存のマッピングが上書きされます。それ以外の場合はエラーが発生します。

`download_info` は、URL とハッシュのタプルを含むオプショナルなベクターです。これらの URL は、このアーティファクトを取得できる可能性のある場所としてリストされます。`lazy` が `true` に設定されている場合、ダウンロード情報が利用可能であっても、このアーティファクトは `artifact"name"` 構文を介してアクセスされるか、`ensure_artifact_installed()` が呼び出されるまでダウンロードされません。
