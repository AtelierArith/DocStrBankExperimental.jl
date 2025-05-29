```
generate_franklin_template()
```

Franklinマークダウンページのテンプレートを生成します。

# キーワード引数

  * `title`: ページタイトル。デフォルトは`nothing`
  * `slug`: ウェブページのURLパスを指定します（ベースパスの後）。デフォルトは`nothing`
  * `tags`: ページに関連するキーワードまたはタグ。デフォルトは`nothing`
  * `description`: ページ内容の説明。デフォルトは`nothing`
  * `rss_title`: RSSフィードに表示されるページタイトル。デフォルトは`nothing`
  * `rss_description`: RSS更新に伴う説明。デフォルトは`nothing`
  * `rss_pubdate`: RSSフィードの発行日。デフォルトは`nothing`

これらのkwargsは、`Franklin.jl`のドキュメントから直接取得される「ページ変数」です。より具体的な詳細については、[ページ変数](https://franklinjl.org/syntax/page-variables/)を参照してください。

# 戻り値

  * さらに修正可能な有効なFranklinテンプレートを含む`String`オブジェクト

# 例

次の呼び出しが行われた場合: `generate_franklin_template(; title = "All-Payer Claims Database", tags = ["apcd", "claims", "database"])`、次の文字列が返されます:

```
+++

title = "All-Payer Claims Database"

tags = ["zettel", "apcd", "claims", "database", "archive"]

+++

```

これは、必要に応じてさらに編集またはフォーマットできます。
