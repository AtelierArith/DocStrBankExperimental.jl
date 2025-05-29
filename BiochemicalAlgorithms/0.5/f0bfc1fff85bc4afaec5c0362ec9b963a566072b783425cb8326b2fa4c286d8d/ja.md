```
read_ball_ini_file(fname::AbstractString, ::Type{T} = Float32) -> BALLIniFile
```

BALLの古いIniファイル形式のファイルを読み込み、BALLIniFileとして返します。

# サポートされているキーワード引数

  * `cleanup_keys::Bool = true` はコロンで区切られたキー名を簡略化します（例：`ver:version` は `version` になり、`key:I` は `I` になりますなど）。
