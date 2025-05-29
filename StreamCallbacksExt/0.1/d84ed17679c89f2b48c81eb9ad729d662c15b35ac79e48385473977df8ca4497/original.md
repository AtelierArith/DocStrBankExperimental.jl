```
extract_tokens(::StreamCallbacks.AnthropicStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

Extract token counts from Anthropic stream chunks. Handles both message_start events with usage information and completion events with output tokens.
