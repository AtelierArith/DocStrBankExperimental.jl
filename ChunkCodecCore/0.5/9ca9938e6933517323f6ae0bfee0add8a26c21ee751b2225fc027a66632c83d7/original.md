```
check_contiguous(x::AbstractVector{UInt8})
```

Check if the given vector is contiguous in memory. Throw an error if the vector is not contiguous or if its length cannot be represented as Int64.
