```
MCPPrompt(; name::String, description::String="", 
        arguments::Vector{PromptArgument}=PromptArgument[], 
        messages::Vector{PromptMessage}=PromptMessage[])
```

Implement a prompt or prompt template as defined in the MCP schema. Prompts can include variables that are replaced with arguments when retrieved.

# Fields

  * `name::String`: Unique identifier for the prompt
  * `description::String`: Human-readable description of the prompt's purpose
  * `arguments::Vector{PromptArgument}`: Arguments that this prompt accepts
  * `messages::Vector{PromptMessage}`: The sequence of messages in the prompt
