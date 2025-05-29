```
is_thread_safe(::Union{Codec, DecodeOptions, EncodeOptions})::Bool
```

Return `true` if it is safe to use the options to encode or decode concurrently in multiple threads.
