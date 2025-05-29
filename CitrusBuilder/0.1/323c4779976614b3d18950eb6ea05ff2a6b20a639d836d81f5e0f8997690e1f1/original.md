```
array_five_point_choice_question(id, language_settings::LanguageSettings; subquestions, kwargs...)
array_five_point_choice_question(id, title::String; subquestions, help=nothing, kwargs...)
array_five_point_choice_question(children::Function, id, language_settings::LanguageSettings; kwargs...)
array_five_point_choice_question(children::Function, id, title::String; kwargs...)
```

Construct an array five point choice question.

For a list of additional keyword arguments see [`Question`](@ref).
