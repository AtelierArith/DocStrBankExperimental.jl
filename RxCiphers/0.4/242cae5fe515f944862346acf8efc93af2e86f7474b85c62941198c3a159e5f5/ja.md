```
DLMSpace
```

文字空間で、部分文字列 `::String` をトークン `::Int` としてエンコードします。`dlm` は、トークン化される部分文字列を区切る区切り文字です。

# フィールド

  * `charmap::Vector{String}` はトークンを部分文字列にマッピングします。`W.charmap[token]` は `substring` を返します。
  * `tokenmap::Dict{String, Int}` は部分文字列を割り当てられたトークンにマッピングします。`W.tokenmap[substring]` は `token` を返します。
  * `dlm` は区切り文字列/文字です。
  * `size::Int` はエンコードされた部分文字列の数 / トークンの数です。
  * `tokens::Vector{Int}` はすべてのエンコードトークンを格納し、反復処理に使用されます。
