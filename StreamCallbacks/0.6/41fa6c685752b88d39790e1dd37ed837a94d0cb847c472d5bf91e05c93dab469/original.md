```
StreamCallback
```

Simplest callback for streaming message, which just prints the content to the output stream defined by `out`. When streaming is over, it builds the response body from the chunks and returns it as if it was a normal response from the API.

For more complex use cases, you can define your own `callback`. See the interface description below for more information.

# Fields

  * `out`: The output stream, eg, `stdout` or a pipe.
  * `flavor`: The stream flavor which might or might not differ between different providers, eg, `OpenAIStream` or `AnthropicStream`.
  * `chunks`: The list of received `StreamChunk` chunks.
  * `verbose`: Whether to print verbose information. If you enable DEBUG logging, you will see the chunks as they come in.
  * `throw_on_error`: Whether to throw an error if an error message is detected in the streaming response.
  * `kwargs`: Any custom keyword arguments required for your use case.

# Interface

  * `StreamCallback(; kwargs...)`: Constructor for the `StreamCallback` object.
  * `streamed_request!(cb, url, headers, input)`: End-to-end wrapper for POST streaming requests.

`streamed_request!` composes of:

  * `extract_chunks(flavor, blob)`: Extract the chunks from the received SSE blob. Returns a list of `StreamChunk` and the next spillover (if message was incomplete).
  * `callback(cb, chunk)`: Process the chunk to be printed

      * `extract_content(flavor, chunk)`: Extract the content from the chunk.
      * `print_content(out, text)`: Print the content to the output stream.
  * `is_done(flavor, chunk)`: Check if the stream is done.
  * `build_response_body(flavor, cb)`: Build the response body from the chunks to mimic receiving a standard response from the API.

If you want to implement your own callback, you can create your own methods for the interface functions. Eg, if you want to print the streamed chunks into some specialized sink or Channel, you could define a simple method just for `print_content`.

# Example

```julia
using PromptingTools
const PT = PromptingTools

# Simplest usage, just provide where to steam the text (we build the callback for you)
msg = aigenerate("Count from 1 to 100."; streamcallback = stdout)

streamcallback = PT.StreamCallback() # record all chunks
msg = aigenerate("Count from 1 to 100."; streamcallback)
# this allows you to inspect each chunk with `streamcallback.chunks`

# Get verbose output with details of each chunk for debugging
streamcallback = PT.StreamCallback(; verbose=true, throw_on_error=true)
msg = aigenerate("Count from 1 to 10."; streamcallback)
```

Note: If you provide a `StreamCallback` object to `aigenerate`, we will configure it and necessary `api_kwargs` via `configure_callback!` unless you specify the `flavor` field. If you provide a `StreamCallback` with a specific `flavor`, we leave all configuration to the user (eg, you need to provide the correct `api_kwargs`).
