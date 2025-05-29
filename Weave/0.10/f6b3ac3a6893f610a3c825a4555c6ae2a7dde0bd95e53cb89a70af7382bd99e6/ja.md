```
notebook(source::AbstractString; kwargs...)
```

Weaveドキュメント`source`をJupyter Notebookに変換し、[`nbconvert`](https://nbconvert.readthedocs.io/en/latest/)を使用してコードを実行します。**すべてのチャンクオプションは無視されます**。

## キーワードオプション

  * `out_path::Union{Symbol,AbstractString} = :pwd`: 出力が生成されるパスは次のいずれかです：

      * `:doc`: ソースドキュメントのパス
      * `:pwd`: Julia作業ディレクトリ（デフォルト）
      * `"somepath"`: 出力ディレクトリの`String`、例：`"~/outdir"`、またはファイル名の例：`"~/outdir/outfile.tex"`
  * `timeout = -1`: nbconvertセルのタイムアウト（秒）。デフォルトは`-1`（タイムアウトなし）
  * `nbconvert_options::AbstractString = ""`: nbconvertに渡す追加オプションの`String`、例：`"--allow-errors"`
  * `jupyter_path::AbstractString = "jupyter"`: 使用したいJupyterのパス/コマンド。デフォルトは`"jupyter"`で、リンクまたはエイリアスされているものを実行します

!!! warning
    コードは***Weave***によってではなく、[`nbconvert`](https://nbconvert.readthedocs.io/en/latest/)によって実行されます。これは、出力が必ずしも常に正しく動作するわけではないことを意味します。詳細は[#116](https://github.com/JunoLab/Weave.jl/issues/116)を参照してください。


!!! note
    WeaveドキュメントをJupyter Notebookに*単に*変換するには、[`convert_doc`](@ref)を代わりに使用してください。

