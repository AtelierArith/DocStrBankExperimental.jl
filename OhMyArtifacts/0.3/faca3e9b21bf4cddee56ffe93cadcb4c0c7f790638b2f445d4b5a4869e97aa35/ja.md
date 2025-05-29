```
bind_my_artifact!(artifacts_toml::String, name::AbstractString, hash::SHA256; force::Bool = false, metadata = nothing)
```

指定された "Artifacts.toml" ファイルに `name` -> `hash` のマッピングを書き込み、使用状況を追跡します。`force` が `true` に設定されている場合、既存のマッピングを上書きします。それ以外の場合はエラーが発生します。`metadata` を設定することで、`artifacts_toml` に `name` エントリのフィールド名 `meta` で追加情報を保存できます。
