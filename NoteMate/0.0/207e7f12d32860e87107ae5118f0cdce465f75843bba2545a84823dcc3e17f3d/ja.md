```
get_title_section
```

タイトルヘッダーの下にあるセクションを取得します。

# 引数

  * `contents`: Julia標準ライブラリ`Markdown.parse`からのMD構造体のコンテンツ構造体の`Vector`
  * `title_headers`: タイトルヘッダーと見なされる`Header`構造体のベクター

# キーワード引数

  * `name_sections = true`: 辞書をベクターの代わりに取得するためのブール設定。

# 戻り値

  * デフォルトでは、"Title"キーの下にあるタイトルセクションの辞書
  * タイトルヘッダーで始まるすべてのセクションテキストのベクター
