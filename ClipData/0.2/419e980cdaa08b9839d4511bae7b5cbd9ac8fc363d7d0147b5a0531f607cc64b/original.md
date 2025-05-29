```
cliparray(t::AbstractVecOrMat; kwargs...)
```

Send a `Vector` or `Matrix` to the clipboard. Default delimiter is tab and with no header. Accepts all keyword arguments that can be passed to `CSV.write`.

# Examples

```julia-repl
julia> """
       1 2
       3 4
       """ |> clipboard

julia> cliparray()
2×2 Matrix{Int64}:
 1  2
 3  4
```
