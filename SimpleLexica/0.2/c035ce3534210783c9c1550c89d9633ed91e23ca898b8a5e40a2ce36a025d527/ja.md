検索辞書 `lex` から文字列 `s` を検索します。

```julia
search(lex, s; searchscope, simplified, case_sensitive)

```

オプションのパラメータ：

  * `searchscope`: `SearchScope.LEMMA`、`SearchScope.ARTICLE`、または `SearchScope.ALL` のいずれか。デフォルト: `SearchScope.ALL`。
  * `simplified`: 検索用にフォーマットされた `Lexicon`。デフォルト: `nothing`。
  * `case_sensitive`: 一致において大文字と小文字を考慮する場合は `true`。デフォルト: `true`。
