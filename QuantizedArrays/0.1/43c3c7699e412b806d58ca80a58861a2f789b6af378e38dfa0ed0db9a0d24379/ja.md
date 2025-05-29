```
CodeBook{U<:Unsigned,T}
```

コードブック構造体。ベクトルプロトタイプに対応するコードと、コードとプロトタイプの間のマッピングを保持します。

# フィールド

  * `codes::Vector{U}` コード
  * `vectors::Matrix{T}` プロトタイプ
  * `codemap::Dict{U,Int}` コードから `vectors` の列へのマッピング
