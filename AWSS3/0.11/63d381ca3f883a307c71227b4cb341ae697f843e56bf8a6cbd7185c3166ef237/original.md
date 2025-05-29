```
read(fp::S3Path; byte_range=nothing)
```

Fetch data from the S3 path as a `Vector{UInt8}`.  A subset of the object can be specified with `byte_range` which should be a contiguous integer range, e.g. `1:4`.
