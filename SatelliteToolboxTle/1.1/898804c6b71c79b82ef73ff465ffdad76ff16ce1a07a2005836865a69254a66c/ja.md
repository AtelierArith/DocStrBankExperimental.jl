```
read_tles(tles::AbstractString; verify_checksum::Bool = true) -> Vector{TLE}
```

文字列`tles`内のTLEのセットを解析します。この関数は解析されたTLEを含む`Vector{TLE}`を返します。

# キーワード

  * `verify_checksum::Bool`: `true`の場合、両方のTLE行のチェックサムが検証されます。そうでない場合、チェックサムは確認されません。（**デフォルト** = `true`）
