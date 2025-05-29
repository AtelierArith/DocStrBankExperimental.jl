```
compressedwordvectors(filename [,type=Float64][; kind=:text])
```

ファイルから `CompressedWordVectors` 型オブジェクトを生成します。

# 引数

  * `filename::AbstractString` 埋め込みファイル名
  * `type::Type` 埋め込みベクトル要素の型; デフォルトは `Float64`

# キーワード引数

  * `kind::Symbol` 埋め込みファイルがテキスト形式（`:text`）かバイナリ形式（`:binary`）かを指定します; デフォルトは `:text`
