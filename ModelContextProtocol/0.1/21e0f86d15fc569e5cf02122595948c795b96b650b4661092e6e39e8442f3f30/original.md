```
PromptMessage(; content::Union{TextContent, ImageContent, EmbeddedResource}, role::Role=user)
```

Represent a single message in a prompt template.

# Fields

  * `content::Union{TextContent, ImageContent, EmbeddedResource}`: The content of the message
  * `role::Role`: Whether this message is from the user or assistant (defaults to user)
