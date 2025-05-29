```
PromptMessage(content::Union{TextContent, ImageContent, EmbeddedResource}) -> PromptMessage
```

Create a prompt message with only content (role defaults to user).

# Arguments

  * `content::Union{TextContent, ImageContent, EmbeddedResource}`: The message content

# Returns

  * `PromptMessage`: A new prompt message with the default user role
