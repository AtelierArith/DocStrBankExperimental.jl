```
language_settings(settings; same_default=false)
language_settings(language, title; same_default=false, kwargs...)
```

Construct `LanguageSettings` for a survey component. Settings for single can either be provided as `settings::Vector{LanguageSetting}` (see also [`language_setting`](@ref)) or a combination of `language` and `title`.

If multiple languages are provided and `same_default=true` then the `default` value of the default language is inherited by all other languages.

# Examples

Simple construction of language settings for a single language:

```julia
language_settings("de", "Ein Titel")
```

If multiple languages are needed, construct settings using a vector of [`language_setting`](@ref)

```julia
language_settings([
    language_setting("en", "A title"),
    language_setting("de", "Ein Titel")
])
```

To inherit the `default` value of the default language, `same_default` can be used

```julia
language_settings([
    language_setting("en", "title", default="placeholder value"),
    language_setting("de", "Titel")
], same_default=true)
```
