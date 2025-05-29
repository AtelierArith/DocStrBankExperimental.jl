```
LRNData
```

`LRNData`は、次のフィールドを持つ`*.lrn`ファイルの内容を表します：

  * `data::Matrix{Float64}`

    データの行列、行にケース、列に変数
  * `column_types::Array{LRNCType, 1}`

    列のタイプ、`LRNCType`を参照
  * `key::Array{Integer, 1}`

    各行のユニークキー
  * `names::Array{String, 1}`

    列名
  * `key_name::String`

    キー列の名前
  * `comment::String`

    データに関するコメント
