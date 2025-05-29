```
default_buffer(::Type{SlabBuffer}) -> SlabBuffer{1048576}
```

Return the current task-local default `SlabBuffer`, if one does not exist in the current task, it will create one automatically. This currently can only create `SlabBuffer{1048576}`, and you cannot adjust the slab size it creates.
