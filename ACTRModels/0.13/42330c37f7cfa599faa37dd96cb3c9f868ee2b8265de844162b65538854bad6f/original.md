```
match(chunk::AbstractChunk; request...)
```

Returns a boolean indicating whether a request matches a chunk. False is returned if the slot does not exist in the chunk or the value of the slot does not match the request value.

# Arguments

  * `chunk::AbstractChunk`: a chunk object

# Keywords

  * `request...`: optional keyword arguments corresponding to critiria for matching chunk
