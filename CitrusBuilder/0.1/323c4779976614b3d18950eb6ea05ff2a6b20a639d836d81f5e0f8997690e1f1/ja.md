```
array_five_point_choice_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_five_point_choice_question(id, title::String; subquestions, help=nothing, kwargs...)
array_five_point_choice_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_five_point_choice_question(children::Function, id, title::String; kwargs...)
```

配列の5ポイント選択質問を構築します。

追加のキーワード引数のリストについては、[`Question`](@ref)を参照してください。
