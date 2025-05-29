```
@debug_output debug_id title data_or_func fmt
```

Same as [`@debug_output`](@ref) with `debug_id`, `title`, `data_or_func` arguments. Additional `fmt` argument specifies an output format. Default is JSON.  Implemented formats are JSON with JSON.jl, HTML and TXT with PrettyTables.jl, and SVG, XML as raw data output.

See details of the `FORMAT_WRITERS` dictionary
