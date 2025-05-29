```
date_select(id, language_settings::LanguageSettings; minimum=nothing, maximum=nothing, kwargs...)
date_select(id, title::String; help=nothing, kwargs...)
```

日付選択の質問を作成します。

# キーワード引数

  * `minimum`: 許可される最小日付
  * `maximum`: 許可される最大日付

追加のキーワード引数のリストについては[`Question`](@ref)を参照してください。
