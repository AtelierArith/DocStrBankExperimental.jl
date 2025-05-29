```
tangle(source::AbstractString; kwargs...)
```

入力ドキュメントから .jl ファイルにソースコードをタンブルします。

## キーワードオプション

  * `informat::Union{Nothing,AbstractString} = nothing`: 入力ドキュメントのフォーマット。デフォルト（すなわち `nothing` が与えられた場合）では、Weave はファイル拡張子に基づいて自動的に設定します。また、`"script"`、`"markdown"`、`"notebook"`、または `"noweb"` のいずれかを指定することもできます。
  * `out_path::Union{Symbol,AbstractString} = :doc`: 出力が生成されるパスは、次のいずれかである必要があります：

      * `:doc`: ソースドキュメントのパス（デフォルト）
      * `:pwd`: Julia 作業ディレクトリ
      * `"somepath"`: 出力ディレクトリの `String` 例：`"~/outdir"`、またはファイル名の例：`"~/outdir/outfile.tex"`
