```
read_tles_from_file(filename::String; verify_checksum::Bool = true) -> Vector{TLE}
```

ファイル `filename` から TLE を読み込み、解析された TLE の `Vector{TLE}` を返します。

# キーワード

  * `verify_checksum::Bool`: `true` の場合、両方の TLE 行のチェックサムが検証されます。そうでない場合、チェックサムは確認されません。（**デフォルト** = `true`）
