```
HrsePrintOptions(kwargs...)
```

HRSE構造体をテキストに印刷するためのオプションを保存します。

# 引数

  * `indent = "  "`: インデントに使用する文字列。
  * `comments = true`: `CommentedElement`オブジェクトからコメントを印刷するかどうか; falseの場合、コメントは無視されます。
  * `extensions`: HRSEへの[`Extension`](@ref)のコレクション。
  * `pairmode = COLON_MODE`: ペアを印刷する際に使用する[`PairMode`](@ref)。
  * `inlineprimitives = 20`: 新しいインデントレベルを追加するのではなく、単一行に印刷するプリミティブのリストの最大文字列長。
  * `trailingnewline = true`: ファイルの最後にトレーリングニューラインを印刷するかどうか。

他にも[`writehrse`](@ref)、[`ashrse`](@ref)を参照してください。
