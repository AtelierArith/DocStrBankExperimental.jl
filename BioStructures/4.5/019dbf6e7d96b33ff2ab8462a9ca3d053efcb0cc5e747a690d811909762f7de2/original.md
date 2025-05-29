```
writemultimmcif(filepath, cifs; gzip=false)
writemultimmcif(io, cifs; gzip=false)
```

Write multiple `MMCIFDict`s as a `Dict{String, MMCIFDict}` to a filepath or stream. The keyword argument `gzip` (default `false`) determines if the output is gzipped.
