```
is_valid_extra_data(ptr::Ptr, remaining_bytes::UInt16)::Bool
```

Check if the chunk of bytes pointed to by `ptr` and `remaining_bytes` onward represent valid gzip metadata for the "extra" field.
