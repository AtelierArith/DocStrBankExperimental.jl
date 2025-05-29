```
multiple_numerical_input(id, language_settings::LanguageSettings; subquestions, kwargs...)
multiple_numerical_input(id, title::String; subquestions, help=nothing, kwargs...)
multiple_numerical_input(children::Function, id, language_settings::LanguageSettings; kwargs...)
multiple_numerical_input(children::Function, id, title::String; kwargs...)
```

Construct a multiple numerical input question.
