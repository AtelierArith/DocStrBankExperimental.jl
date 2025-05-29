```
multiple_numerical_input(id, language_settings::LanguageSettings; subquestions, kwargs...)
multiple_numerical_input(id, title::String; subquestions, help=nothing, kwargs...)
multiple_numerical_input(children::Function, id, language_settings::LanguageSettings; kwargs...)
multiple_numerical_input(children::Function, id, title::String; kwargs...)
```

複数の数値入力質問を構築します。
