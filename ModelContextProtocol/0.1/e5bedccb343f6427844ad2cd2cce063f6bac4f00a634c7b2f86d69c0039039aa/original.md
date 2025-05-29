```
GetPromptResult(; description::String, messages::Vector{PromptMessage}) <: ResponseResult
```

Result returned from a get prompt request.

# Fields

  * `description::String`: Description of the prompt
  * `messages::Vector{PromptMessage}`: The prompt messages with template variables replaced
