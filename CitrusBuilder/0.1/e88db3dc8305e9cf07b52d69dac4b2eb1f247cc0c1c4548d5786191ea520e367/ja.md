```
array_increase_decrease_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_increase_decrease_question(id, title::String; subquestions, help=nothing, kwargs...)
array_increase_decrease_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_increase_decrease_question(children::Function, id, title::String; kwargs...)
```

配列の増加/減少に関する質問を構築します。

追加のキーワード引数のリストについては、[`Question`](@ref)を参照してください。
