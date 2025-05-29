```
seek(f::FLACDecoder, offset::Int64)
```

Perform an absolute seek within the given FLAC stream.  Throws an `ArgumentError` if the requested seek is impossible.  Will automatically `flush()` the decoder stream if a seek error is encountered.
