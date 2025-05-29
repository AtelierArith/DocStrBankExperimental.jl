```
default_buffer(::Type{AllocBuffer}) -> AllocBuffer{Vector{UInt8}}
```

Return the current task-local default `AllocBuffer`, if one does not exist in the current task, it will create one automatically. This currently can only create `AllocBuffer{Vector{UInt8}}`, and you cannot adjust the memory size it creates (1048576 bytes).
