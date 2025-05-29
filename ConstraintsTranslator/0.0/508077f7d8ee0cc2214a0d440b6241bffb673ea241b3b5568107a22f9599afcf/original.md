```
format_template(template::PromptTemplate; kwargs...)::Prompt
```

Formats a `PromptTemplate` by substituting all variables in the system and user messages with user-provided values.

# Arguments

  * `template::PromptTemplate`: The prompt template containing metadata, system, and user messages.
  * `kwargs...`: A variable number of keyword arguments where keys are variable names and values are the corresponding replacements.

# Returns

  * `Prompt`: A `Prompt` struct with the system and user messages containing the substituted values.

# Raises

  * `ErrorException`: If any variables specified in the system or user templates are not present in the `kwargs`.
  * `Warning`: If there are extra `kwargs` that are not used in the templates.
