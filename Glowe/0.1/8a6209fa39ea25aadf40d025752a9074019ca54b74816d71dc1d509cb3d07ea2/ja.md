```
wordvectors(filename [,type=Float64][; kind=:text, header=false, normalize=true, vocabulary=nothing])
```

ファイルからWordVectors型オブジェクトを生成します。

# 引数

  * `filename::AbstractString` 埋め込みファイル名
  * `type::Type` 埋め込みベクトル要素の型; デフォルトは `Float64`

# キーワード引数

  * `kind::Symbol` 埋め込みファイルがテキスト形式（`:text`）か

バイナリ形式（`:binary`）かを指定します; デフォルトは `:text`

  * `header::Union{Nothing, Bool}` テキスト埋め込みファイルでは

ファイルにヘッダー（行数、列数）が含まれているかどうかを指定します。ヘッダーが `nothing` の場合、ローダーはヘッダーの存在を自動検出しようとします; デフォルトは `nothing`

  * `normalize:Bool` 埋め込みベクトルを正規化するかどうかを指定します

すなわち、単位ベクトルを返すかどうか; デフォルトは true

  * `vocabulary::Union{Nothing, AbstractString}` `vocab_count` で生成された語彙

ファイルへのパス（バイナリ埋め込みに必要）; デフォルトは `nothing`

  * `load_bias::Bool` バイナリ埋め込みファイルを使用する場合に

バイアス項を読み込むかどうかを指定します; デフォルトは `false`
