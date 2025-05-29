```
array_yes_no_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_yes_no_question(id, title::String; subquestions, help=nothing, kwargs...)
array_yes_no_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_yes_no_question(children::Function, id, title::String; kwargs...)
```

配列のはい/いいえ質問を構築します。

追加のキーワード引数のリストについては、[`Question`](@ref)を参照してください。
