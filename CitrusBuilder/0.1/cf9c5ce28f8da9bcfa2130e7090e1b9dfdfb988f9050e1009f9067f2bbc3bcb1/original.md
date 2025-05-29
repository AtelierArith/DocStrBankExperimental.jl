```
language_setting(language, title; kwargs...)
```

Construct a `LanguageSetting` for a survey component.

# Arguments

  * `language`: A language code. For a list of all available languages see https://translate.limesurvey.org/languages/
  * `title`: The title of the survey component

# Keyword arguments

  * `description`: A description of the survey component
  * `help`: A help text that is displayed for the survey component (questions only)
  * `default`: The default value of the survey component (questions only)

# Examples

```julia
language_setting("en", "title")
language_setting("en", "question title", help="some help for survey participants")
```
