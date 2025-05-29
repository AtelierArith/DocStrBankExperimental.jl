```
TEXDocument(contents::AbstractString, add_defaults::Bool; requires, preamble, class, classoptions)
```

このコンストラクタ関数は、`teximg`に渡すことができる`TEXDocument`型の`struct`を作成します。すべての引数は文字列として渡す必要があります。

`add_defaults`が`false`の場合、ドキュメント構造は*自動的に*追加されません。この場合、キーワード引数は無視され、`contents`は完全なLaTeXドキュメントでなければなりません。

利用可能なキーワード引数は次のとおりです：

  * `requires`: プレアンブルの`documentclass`の前に来るコード。デフォルト: `raw"\RequirePackage{luatex85}"`。
  * `class`: ドキュメントクラス。デフォルト（および使用すべきもの）: `"standalone"`。
  * `classoptions`: クラスに渡すべきオプション、すなわち、`\documentclass[$classoptions]{$class}`。デフォルト: `"preview, tightpage, 12pt"`。
  * `preamble`: プレアンブル用の任意のコード（`\documentclass`と`\begin{document}`の間）。デフォルト: `raw"\usepackage{amsmath, xcolor} \pagestyle{empty}"`。

さらに[`CachedTEX`](@ref)、[`compile_latex`](@ref)なども参照してください。
