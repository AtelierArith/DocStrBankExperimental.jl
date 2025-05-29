```
array_increase_decrease_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_increase_decrease_question(id, title::String; subquestions, help=nothing, kwargs...)
array_increase_decrease_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_increase_decrease_question(children::Function, id, title::String; kwargs...)
```

Construct an array increase/decrease question.

For a list of additional keyword arguments see [`Question`](@ref).
