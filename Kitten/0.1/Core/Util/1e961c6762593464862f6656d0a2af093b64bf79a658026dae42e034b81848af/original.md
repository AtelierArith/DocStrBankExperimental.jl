```
json(content::Vector{UInt8}; status::Int, headers::Vector{Pair}) :: HTTP.Response
```

A helper function that can be passed binary data that should be interpreted as JSON.  No conversion is done on the content since it's already in binary format.
