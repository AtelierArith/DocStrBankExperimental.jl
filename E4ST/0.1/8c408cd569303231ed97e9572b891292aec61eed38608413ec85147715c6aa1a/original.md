```
make_out_path!(config) -> nothing
```

If `config[:out_path]` provided, does nothing.  Otherwise, makes sure `config[:base_out_path]` exists, making it as needed.  Creates a new time-stamped folder via [`time_string`](@ref), stores it into `config[:out_path]`.  See [`get_out_path`](@ref) to create paths for output files. 
