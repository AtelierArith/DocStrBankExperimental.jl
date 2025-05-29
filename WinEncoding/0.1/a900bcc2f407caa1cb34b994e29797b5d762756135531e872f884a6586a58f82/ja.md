```
decode950(a::Vector{UInt8})
```

エンコーディング `cp950/big5/hkscs` で表されるテキストのバイト配列 `a` を文字列に変換します。

  * big5-hkscs または '�' にフォールバック; 無効なシーケンスエラーなし
  * ノンブロッキング

    decode950(f::Filename)

ファイル `f` の内容を cp950 から utf-8 へ Vector{UInt8} に変換します。

## 例

```jldoctest
julia> decode950([0xa4,0x48])
"人"
```
