```
extract_cdp_result(response::Dict, path::Vector{String}=["result", "result", "value"])
```

Extract values from CDP responses with configurable path traversal. Returns the extracted value or nothing if the path doesn't exist.
