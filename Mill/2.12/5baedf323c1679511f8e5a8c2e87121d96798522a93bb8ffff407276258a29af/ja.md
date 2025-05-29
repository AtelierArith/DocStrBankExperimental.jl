```
Mill.string_start_code!(c::Integer; persist=false)
```

新しい値を抽象文字列開始文字のコードポイントとして使用される `string_start_code` パラメータに `c` を設定します。パラメータのデフォルト値は `0x02` で、これは ASCII エンコーディングにおける `STX` 文字に対応します。

`c` は `UInt8` に収まる必要があります。

`persist=true` を設定すると、この設定がセッション間で持続します。

関連情報: [`Mill.string_start_code`](@ref), [`Mill.string_end_code`](@ref), [`Mill.string_end_code!`](@ref).
