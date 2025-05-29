```
StreamCallbackWithTokencounts(; 
    out=stdout, 
    flavor=nothing, 
    chunks=StreamChunk[], 
    verbose=false,
    throw_on_error=false,
    kwargs=NamedTuple(),
    total_tokens=TokenCounts(),
    model=nothing,
    token_formatter=default_token_formatter,
    content_formatter=default_content_formatter,
    timing=RunInfo()
)
```

A stream callback that tracks token usage, costs, and timing information.

# Arguments

  * `out`: Output IO stream (default: stdout)
  * `flavor`: Stream format handler (OpenAI/Anthropic)
  * `chunks`: Vector to store stream chunks
  * `verbose`: Enable verbose logging
  * `throw_on_error`: Whether to throw errors
  * `kwargs`: Additional keyword arguments
  * `total_tokens`: Accumulated token counts
  * `model`: Model identifier
  * `token_formatter`: Function to format token statistics
  * `content_formatter`: Function to format streamed content
  * `timing`: Timing information

# Example

cb = StreamCallbackWithTokencounts(     out = stdout,     flavor = StreamCallbacks.OpenAIStream() )
