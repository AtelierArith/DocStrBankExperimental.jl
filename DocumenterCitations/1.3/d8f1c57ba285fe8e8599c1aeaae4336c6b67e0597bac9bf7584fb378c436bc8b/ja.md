Documenter.jlで文献引用を有効にするためのプラグイン。

```julia
bib = CitationBibliography(bibfile; style=:numeric)
```

は、[`Documenter.makedocs`](https://documenter.juliadocs.org/stable/lib/public/#Documenter.makedocs)の`plugins`キーワード引数の要素として渡す必要があるプラグインオブジェクトをインスタンス化します。

# 引数

  * `bibfile`: データを読み込むための[BibTeX](https://www.bibtex.com/g/bibtex-format/)ファイルの名前。
  * `style`: 文献目録とすべての引用に使用するスタイル。利用可能な組み込みスタイルは、`:numeric`（デフォルト）、`:authoryear`、および`:alpha`です。ユーザー定義スタイルの場合、これは任意の名前またはオブジェクトである可能性があります。

# 内部フィールド

以下の内部フィールドは、引用パイプラインのステップで使用されます。これらは安定したAPIの一部とは見なされるべきではありません。

  * `entries`: `bibfile`内のエントリへの引用キーの辞書
  * `citations`: 引用キーから引用番号への順序付き辞書
  * `page_citations`: ページに引用された引用キーのセットへのページファイル名の辞書。
  * `anchor_map`: 文献ブロック内の参照のリンクアンカーを追跡する[`AnchorMap`](https://documenter.juliadocs.org/stable/lib/internals/anchors/#Documenter.AnchorMap)オブジェクト
