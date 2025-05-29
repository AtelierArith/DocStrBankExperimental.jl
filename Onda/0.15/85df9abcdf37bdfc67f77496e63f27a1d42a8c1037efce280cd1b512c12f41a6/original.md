```
finalize_lpcm_stream(stream::AbstractLPCMStream)::Bool
```

Finalize `stream`, returning `true` if the underlying I/O object used to construct `stream` is still open and usable. Otherwise, return `false` to indicate that underlying I/O object was closed as result of finalization.
