```
ParseStream(text::AbstractString,          index::Integer=1; version=VERSION)
ParseStream(text::IO;                                        version=VERSION)
ParseStream(text::Vector{UInt8},           index::Integer=1; version=VERSION)
ParseStream(ptr::Ptr{UInt8}, len::Integer, index::Integer=1; version=VERSION)
```

さまざまな形式の入力から `ParseStream` を構築します：

  * 文字列（`String` および `SubString` の場合はゼロコピー）
  * `IO` オブジェクト（`IOBuffer` の場合はゼロコピー）。`IO` オブジェクトはシーク可能でなければなりません。
  * バイトのバッファ（ゼロコピー）。呼び出し元は `(ptr,len)` として渡されたバッファを保持する責任があります。

バイトの `index` を解析を開始する位置として提供できます。

`ParseStream` は、ソーステキスト入力をトークンにレキシングし、パーサーのために無視される空白トークンを管理し、出力トークンとツリーノードを一対の出力配列に格納するための IO インターフェースを提供します。

`version`（デフォルトは `VERSION`）は、任意の Julia バージョン `>= v"1.0"` に構文バージョンを設定するために使用できます。私たちは、v"1.0" 以降に追加されたすべての Julia 構文を解析することを目指しており、要求された `version` と互換性がない場合はエラーを出力します。
