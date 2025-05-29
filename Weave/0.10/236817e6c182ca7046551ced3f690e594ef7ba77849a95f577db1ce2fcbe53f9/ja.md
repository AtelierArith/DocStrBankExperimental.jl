```
convert_doc(infile::AbstractString, outfile::AbstractString; outformat::Union{Nothing,AbstractString} = nothing)
```

Weaveドキュメントを異なるフォーマット間で変換します

  * `infile`: 入力ドキュメントのパス
  * `outfile`: 出力ドキュメントのパス
  * `outformat = nothing`: 出力ドキュメントのフォーマット（オプション）。デフォルトでは（すなわち`nothing`が与えられた場合）、Weaveは`outfile`の拡張子から自動的に検出しようとします。また、`"script"`、`"markdown"`、`"notebook"`、または`"noweb"`のいずれかを指定することもできます。
