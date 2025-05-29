```
StreamChunk
```

A chunk of streaming data. A message is composed of multiple chunks.

# Fields

  * `event`: The event name.
  * `data`: The data chunk.
  * `json`: The JSON object or `nothing` if the chunk does not contain JSON.
