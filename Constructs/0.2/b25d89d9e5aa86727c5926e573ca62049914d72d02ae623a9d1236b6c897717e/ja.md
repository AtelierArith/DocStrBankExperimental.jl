```
PaddedString([T], n, [encoding]) -> Construct{T}
```

`n` バイトにパディングされた文字列。

# 引数

  * `T<:AbstractString`: 基本となる文字列の型。
  * `n::Integer`: バイト単位の文字列のサイズ。
  * `encoding::Union{Encoding, String}`: 文字列のエンコーディング。
