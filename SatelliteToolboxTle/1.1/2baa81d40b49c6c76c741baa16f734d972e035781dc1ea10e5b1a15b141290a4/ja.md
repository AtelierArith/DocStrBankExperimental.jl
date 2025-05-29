```
read_tle(l1::AbstractString, l2::AbstractString; kwargs...) -> TLE
```

最初の行が `l1` で、2 番目の行が `l2` の TLE を読み込みます。

# キーワード

  * `name::AbstractString`: 返される TLE オブジェクトの衛星名。   (**デフォルト** = "UNDEFINED")
  * `verify_checksum::Bool`: `true` の場合、両方の TLE 行のチェックサムが検証されます。   そうでない場合、チェックサムは確認されません。 (**デフォルト** = `true`)
