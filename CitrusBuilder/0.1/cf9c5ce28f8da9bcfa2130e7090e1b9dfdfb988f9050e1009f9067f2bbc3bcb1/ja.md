```
language_setting(language, title; kwargs...)
```

調査コンポーネントのための `LanguageSetting` を構築します。

# 引数

  * `language`: 言語コード。利用可能なすべての言語のリストについては https://translate.limesurvey.org/languages/ を参照してください。
  * `title`: 調査コンポーネントのタイトル

# キーワード引数

  * `description`: 調査コンポーネントの説明
  * `help`: 調査コンポーネントに表示されるヘルプテキスト（質問のみ）
  * `default`: 調査コンポーネントのデフォルト値（質問のみ）

# 例

```julia
language_setting("en", "title")
language_setting("en", "question title", help="some help for survey participants")
```
