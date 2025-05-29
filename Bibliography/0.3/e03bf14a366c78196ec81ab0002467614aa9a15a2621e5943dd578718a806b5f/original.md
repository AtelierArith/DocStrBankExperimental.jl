```
export_cff(e::Entry, destination::String="CITATION.cff", version::String="1.2.0", add_preferred::Bool=true) -> Dict{String, Any}
```

Export an `Entry` to a CFF file (default is `CITATION.cff`).
