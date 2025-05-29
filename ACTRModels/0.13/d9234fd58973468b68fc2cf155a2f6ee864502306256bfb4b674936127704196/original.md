```
match(chunk::AbstractChunk, funs...; request...)
```

Returns a boolean indicating whether a request matches a chunk. False is returned if the slot does not exist in the chunk or the value of the slot does not match the request value.

  * `chunk::AbstractChunk`: chunk object
  * `funs...`: a list of functions such as `!=, ==`
  * `request...`: a NamedTuple of slot value pairs
