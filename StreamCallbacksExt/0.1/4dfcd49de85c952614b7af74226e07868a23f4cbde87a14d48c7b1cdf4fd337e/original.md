```
StreamCallbackWithHooks(; kwargs...)
```

A stream callback that combines token counting with customizable hooks for various events.

# Fields

  * `out`: Output IO stream (default: stdout)
  * `flavor`: Stream format handler (OpenAI/Anthropic)
  * `chunks`: Vector to store stream chunks
  * `verbose`: Enable verbose logging
  * `throw_on_error`: Whether to throw errors
  * `kwargs`: Additional keyword arguments
  * `total_tokens`: Accumulated token counts
  * `model`: Model identifier
  * `token_formatter`: Function to format token statistics
  * `timing`: Timing information

# Hooks

  * `content_formatter`: Function to process and format content text
  * `on_meta_usr`: Handler for user token counts/metadata
  * `on_meta_ai`: Handler for AI token counts/metadata
  * `on_error`: Error handler
  * `on_done`: Completion handler
  * `on_start`: Start handler

# Example

```julia
cb = StreamCallbackWithHooks(
    on_meta_ai = (tokens, cost, elapsed) -> println("AI: $(tokens.output) tokens")
)
```
