```
NCharSpace{N}
```

文字空間で、部分文字列 `::String` をトークン `::Int` としてエンコードします。`N` は整数パラメータで、エンコードされた部分文字列の長さ（文字数）を示します。

# フィールド

  * `charmap::Vector{String}` はトークンを部分文字列にマッピングします。`W.charmap[token]` は `substring` を返します。
  * `tokenmap::Dict{String, Int}` は部分文字列を割り当てられたトークンにマッピングします。`W.tokenmap[substring]` は `token` を返します。
  * `units::Vector{String}` はエンコードされた部分文字列の最も簡略化されたバージョンを格納します。
  * `unit_length::Int` は個々のユニットの長さを格納します。
  * `linear::LinearIndices` は複合 n トークンを n ユニットトークンにマッピングします。
  * `cartesian::CartesianIndices` は n ユニットトークンを単一の複合 n トークンにマッピングします。
  * `size::Int` はエンコードされた部分文字列の数 / トークンの数です。
  * `tokens::Vector{Int}` はすべてのエンコードトークンを格納し、反復処理に使用されます。
