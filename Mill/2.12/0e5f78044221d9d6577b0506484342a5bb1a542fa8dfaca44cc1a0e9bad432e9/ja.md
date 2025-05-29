```
Mill.string_end_code!(c::Integer; persist=false)
```

抽象文字列の終端文字のコードポイントとして使用される `string_end_code` パラメータに新しい値を `c` に設定します。パラメータのデフォルト値は `0x03` で、これは ASCII エンコーディングにおける `ETX` 文字に対応します。

`c` は `UInt8` に収まる必要があります。

`persist=true` を設定すると、この設定がセッション間で持続します。

参照: [`Mill.string_end_code`](@ref), [`Mill.string_start_code`](@ref), [`Mill.string_start_code!`](@ref).
