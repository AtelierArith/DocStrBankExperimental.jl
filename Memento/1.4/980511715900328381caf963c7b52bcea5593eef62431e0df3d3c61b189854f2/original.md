```
DefaultHandler(
    io::O,
    fmt::F=DefaultFormatter(),
    opts=Dict{Symbol, Any}();
    levels=nothing,
) where {F<:Formatter, O<:IO}
```

Creates a DefaultHandler with the specified IO type.

# Arguments

  * `io::IO`: the IO type
  * `fmt::Formatter`: the Formatter to use (default to `DefaultFormatter()`)
  * `opts::Dict`: the optional arguments (defaults to `Dict{Symbol, Any}()`)
