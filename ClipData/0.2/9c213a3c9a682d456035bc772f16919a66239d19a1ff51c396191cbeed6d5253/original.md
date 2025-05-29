```
cliptable(; kwargs...)
```

Make a table from the clipboard. Returns a `CSV.File`, which can then be transformed into a `DataFrame` or other Tables.jl-compatible object.

`cliptable` auto-detects delimiters, and all keyword arguments are passed directly to the `CSV.File` constructor.

## Examples

```julia-repl
julia> # Send string to the clipboard
       """
       a, b
       1, 2
       100, 200
       """ |> clipboard

julia> cliptable()
2-element CSV.File{false}:
 CSV.Row: (a = 1,  b = 2)
 CSV.Row: (a = 100,  b = 200)
```
