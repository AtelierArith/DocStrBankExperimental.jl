```
array_question(id, language_settings::LanguageSettings, options::VectorOrElemenet{ResponseScale}; subquestions, type="default", kwargs...)
array_question(id, title::String, options::VectorOrElement{ResponseScale}; help=nothing, kwargs...)
array_question(children::Function, id, language_settings::LanguageSettings, options; kwargs...)
array_question(children::Function, id, title::String, options; kwargs...)
```

Construct an array question.

Specify the question `type` to determine which kind of array question is to be constructed. If `type="dual"` then an array of 2 [`ResponseScale`](@ref) must be provided. Otherwise a single [`ResponseScale`](@ref) is required.

# Available types

  * `"default"`: Array
  * `"text"`: Array (Texts)
  * `"dropdown"`: Array (Numbers)
  * `"dual"`: Array dual scale
  * `"bycolumn"`: Array by column
