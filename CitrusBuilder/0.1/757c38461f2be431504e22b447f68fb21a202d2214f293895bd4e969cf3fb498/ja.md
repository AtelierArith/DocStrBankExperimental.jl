```
array_ten_point_choice_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_ten_point_choice_question(id, title::String; subquestions, help=nothing, kwargs...)
array_ten_point_choice_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_ten_point_choice_question(children::Function, id, title::String; kwargs...)
```

配列の10ポイント選択質問を構築します。

追加のキーワード引数のリストについては、[`Question`](@ref)を参照してください。
