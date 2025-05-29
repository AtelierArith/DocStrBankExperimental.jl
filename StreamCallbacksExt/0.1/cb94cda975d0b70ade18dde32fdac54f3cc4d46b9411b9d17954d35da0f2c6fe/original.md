```
extract_stop_sequence(::StreamCallbacks.OpenAIStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

Extract stop sequence from OpenAI stream chunks. Handles both delta.stop*sequence and finish*reason="stop".
