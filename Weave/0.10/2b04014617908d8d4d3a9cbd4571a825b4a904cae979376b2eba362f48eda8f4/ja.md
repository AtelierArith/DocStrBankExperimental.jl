```
weave(source::AbstractString; kwargs...)
```

入力ドキュメントを出力ファイルに織り込む。

## キーワードオプション

  * `doctype::Union{Nothing,AbstractString} = nothing`: 出力ドキュメント形式。デフォルト（すなわち `nothing` が与えられた場合）では、Weave はファイル拡張子に基づいて自動的に設定します。また、手動で指定することもできます。サポートされている形式については [`list_out_formats()`](@ref) を参照してください。
  * `informat::Union{Nothing,AbstractString} = nothing`: 入力ドキュメント形式。デフォルト（すなわち `nothing` が与えられた場合）では、Weave はファイル拡張子に基づいて自動的に設定します。また、`"script"`、`"markdown"`、`"notebook"`、または `"noweb"` のいずれかを指定することもできます。
  * `out_path::Union{Symbol,AbstractString} = :doc`: 出力が生成されるパスは次のいずれかです：

      * `:doc`: ソースドキュメントのパス（デフォルト）
      * `:pwd`: Julia 作業ディレクトリ
      * `"somepath"`: 出力ディレクトリの `String` 例：`"~/outdir"`、またはファイル名の例：`"~/outdir/outfile.tex"`
  * `args::Any = Dict()`: `weave` 中に `WEAVE_ARGS` として利用可能なランタイムオブジェクト
  * `mod::Union{Module,Nothing} = nothing`: Weave がコードを `eval` するモジュール。`Module` オブジェクトを渡すことができます。そうでなければ、新しいサンドボックスモジュールを作成します。
  * `fig_path::Union{Nothing,AbstractString} = nothing`: 図が生成される場所、`out_path` に対して相対的。デフォルト（すなわち `nothing` が与えられた場合）では、Weave は自動的に `figures` ディレクトリを作成します。
  * `fig_ext::Union{Nothing,AbstractString} = nothing`: 保存される図の拡張子例：`".pdf"`、`".png"`。デフォルト設定は `doctype` に依存します。
  * `cache_path::AbstractString = "cache"`: キャッシュされた出力が保存される場所
  * `cache::Symbol = :off`: コードのキャッシングを制御します：

      * `:off` はキャッシングなし（デフォルト）
      * `:all` はすべてをキャッシュ
      * `:user` はチャンクオプションに基づいてキャッシュ
      * `:refresh` はすべてのコードチャンクを実行し、新しいキャッシュを保存します。
  * `template::Union{Nothing,AbstractString,Mustache.MustacheTokens} = nothing`: `md2html` または `md2tex` 形式のためのテンプレート（ファイルパス）または `Mustache.MustacheTokens`
  * `css::Union{Nothing,AbstractString} = nothing`: md2html 形式に使用される CSS ファイルのパス
  * `highlight_theme::Union{Nothing,Type{<:Highlights.AbstractTheme}} = nothing`: 構文ハイライトに使用されるテーマ（デフォルトは `Highlights.Themes.DefaultTheme`）
  * `pandoc_options::Vector{<:AbstractString} = String[]`: `pandoc2html` および `pandoc2pdf` 形式のために pandoc に渡すオプションの `String` 例：`["--toc", "-N"]`
  * `latex_cmd::Vector{<:AbstractString} = ["xelatex", "-shell-escape", "-halt-on-error"]`: .tex から PDF ファイルを作成するために使用されるコマンド
  * `keep_unicode::Bool = false`: `true` の場合、ユニコード文字をそれぞれの LaTeX 表現に変換しません。これは、ユニコード文字をサポートするフォントと TeX エンジンを使用する場合に特に便利です。

!!! note
    ターミナルから Weave を実行し、IJulia や ESS からの織り込みを避けるようにしてください。これらは出力のキャプチャを混乱させる傾向があります。

