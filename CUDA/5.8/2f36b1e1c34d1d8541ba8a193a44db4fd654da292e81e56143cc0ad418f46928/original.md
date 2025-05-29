```
legacy_stream()
```

Return a special object to use use an implicit stream with legacy synchronization behavior.

You can use this stream to perform operations that should block on all streams (with the exception of streams created with `STREAM_NON_BLOCKING`). This matches the old pre-CUDA 7 global stream behavior.
