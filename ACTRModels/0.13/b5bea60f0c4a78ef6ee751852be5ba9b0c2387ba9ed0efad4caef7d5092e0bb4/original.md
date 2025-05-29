```
compute_activation!(actr, chunk::AbstractChunk; request...)
```

Computes the activation of a chunk. By default, current time is computed  with `get_time`.

# Arguments

  * `actr`: actr object
  * `chunk::AbstractChunk`: a chunk.

# Keywords

  * `request...`: optional keywords for the retrieval request
