```
MCPPrompt(name::String, description::String, arguments::Vector{PromptArgument}, text::String) -> MCPPrompt
```

Create a prompt with a single text message.

# Arguments

  * `name::String`: Unique identifier for the prompt
  * `description::String`: Human-readable description
  * `arguments::Vector{PromptArgument}`: Arguments the prompt accepts
  * `text::String`: Text content for the prompt message

# Returns

  * `MCPPrompt`: A new prompt with a single user message containing the text
