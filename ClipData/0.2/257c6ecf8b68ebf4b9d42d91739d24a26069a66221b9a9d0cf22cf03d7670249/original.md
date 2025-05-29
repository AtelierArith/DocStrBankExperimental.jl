```
cliparray(; kwargs...)
```

Make a `Vector` or `Matrix` from the clipboard. Auto-detects delimiters, and all keyword arguments are passed directly to a `CSV.File` constructor. If the returned `CSV.File` has one column, `cliparray` returns a `Vector`. Otherwise, it returns a `Matrix`.

# Examples

```julia-repl
julia> # Send string to clipboard
       """
       1 2
       3 4
       """ |> clipboard

julia> cliparray()
2×2 Matrix{Int64}:
 1  2
 3  4

julia> """
       1
       2
       3
       4
       """ |> clipboard

julia> cliparray()
4-element Vector{Int64}:
 1
 2
 3
 4
```
