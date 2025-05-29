```
find!(s::Hex, sigstr::AbstractString, start=nothing)
```

search for binary signature and return the offset or nothing;  modify s._offset to point to beginning of located signature
