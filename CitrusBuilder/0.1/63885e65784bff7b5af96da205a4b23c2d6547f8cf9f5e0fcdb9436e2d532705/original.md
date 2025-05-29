```
array_yes_no_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_yes_no_question(id, title::String; subquestions, help=nothing, kwargs...)
array_yes_no_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_yes_no_question(children::Function, id, title::String; kwargs...)
```

Construct an array yes/no question.

For a list of additional keyword arguments see [`Question`](@ref).
