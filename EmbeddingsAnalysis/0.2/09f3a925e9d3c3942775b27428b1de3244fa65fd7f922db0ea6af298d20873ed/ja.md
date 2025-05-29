```
write2disk(filename::AbstractString, wv::CompressedWordVectors [;kind=:binary])
```

圧縮された埋め込みをディスクに書き込みます。

# 引数

  * `filename::AbstractString` 埋め込みファイル名
  * `wv::CompressedWordVectors` 埋め込み

# キーワード引数

  * `kind::Symbol` 埋め込みファイルがテキスト形式（`:text`）かバイナリ形式（`:binary`）かを指定します；デフォルトは `:binary`
