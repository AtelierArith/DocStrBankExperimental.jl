```
NullTerminatedString([T], [encoding]) -> Construct{T}
```

ヌル文字で終わる文字列。

これは `AbstractString` のサブタイプのデフォルト構造体です。

# 引数

  * `T<:AbstractString`: 基本となる文字列型。
  * `encoding::Union{Encoding, String}`: 文字列のエンコーディング。
