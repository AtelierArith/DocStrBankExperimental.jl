```
decode1252(a::Vector{UInt8})
```

`cp1252/windows-1252`エンコーディングで表現されたバイトの配列`a`を文字列に変換します。

  * [0x8d] => '\u8d' はWindows APIと同様
  * 無効なシーケンスエラーなし
  * ノンブロッキング

## 例

```jldoctest
julia> decode1252([0x80])
"€"

julia> decode1252([0xa9])
"©"

```
