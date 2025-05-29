```
search_appendix(s::Symbol, args..., kwargs...)
```

付録で変数名を検索します。

## 引数

  * `s::Symbol`: Fred MDの場合は`:MD`、Fred QDの場合は`:QD`であるべきです。
  * `needle::Union{String, Regex}`: 付録で見つけるパターン。

## キーワード引数

  * `case_sensitive::Bool=false`: 検索は大文字と小文字を区別しますか？
  * `historic::Bool=false`: 検索は現在の付録または歴史的な付録のどちらですか？

## 戻り値

  * 付録内のすべての一致を含む`DataFrame`を返します。
