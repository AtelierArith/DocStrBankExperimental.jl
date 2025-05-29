```
DefaultHandler(
    filename::AbstractString,
    fmt::F=DefaultFormatter(),
    opts=Dict{Symbol, Any}();
    levels=nothing,
) where {F<:Formatter}
```

Creates a DefaultHandler with a IO handle to the specified filename.

# Arguments

  * `filename::AbstractString`: the filename of a log file to write to
  * `fmt::Formatter`: the Formatter to use (default to `DefaultFormatter()`)
  * `opts::Dict`: the optional arguments (defaults to `Dict{Symbol, Any}()`)
