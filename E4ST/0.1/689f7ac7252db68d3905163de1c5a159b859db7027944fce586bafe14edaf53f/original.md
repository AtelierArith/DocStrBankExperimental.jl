```
process_results!(config; processed=true) -> data
```

This reads `data` in, then calls [`process_results!(config, data)`](@ref).  

  * `processed=false` - reads in `data` via [`read_parsed_results`](@ref)
  * `processed=true` - reads in `data` via [`read_processed_results`](@ref)
