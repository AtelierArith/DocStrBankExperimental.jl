```
extract_tokens(::StreamCallbacks.OpenAIStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

Extract token counts from OpenAI stream chunks. Handles:

  * Legacy format with prompt*tokens and completion*tokens
  * Cache hit/miss statistics
  * Detailed token breakdowns (cached*tokens, audio*tokens)
  * End-of-stream combined usage statistics
