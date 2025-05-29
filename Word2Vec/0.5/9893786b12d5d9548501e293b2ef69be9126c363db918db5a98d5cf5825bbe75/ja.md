```
wordvectors(filename [,type=Float64][; kind=:text, skip=false, normalize=true, fasttext=false])
```

ファイルからWordVectors型オブジェクトを生成します。

# 引数

  * `filename::AbstractString` 埋め込みファイル名
  * `type::Type` 埋め込みベクトル要素の型; デフォルトは `Float64`

# キーワード引数

  * `kind::Symbol` 埋め込みファイルがテキスト形式（`:text`）か

バイナリ形式（`:binary`）かを指定します; デフォルトは `:text`

  * `skip::Bool` バイナリ埋め込みファイルでは、改行

バイトが欠落しているかどうかを指定します（Googleの事前学習モデルには`true`を使用）; デフォルトは `false`

  * `normalize:Bool` 埋め込みベクトルを正規化するかどうかを指定します

すなわち、単位ベクトルを返します; デフォルトは `true`

  * `delim:Char` デリミタ; デフォルトは `' '`
  * `fasttext::Bool` `true`に設定すると、パース前に行を削除しないことで発生するバグが修正されます。オプションはバイナリ形式では無視されます; デフォルトは `false`
