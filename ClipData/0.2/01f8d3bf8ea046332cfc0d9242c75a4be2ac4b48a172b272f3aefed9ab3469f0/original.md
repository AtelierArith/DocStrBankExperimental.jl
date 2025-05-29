```
cliptable(t; delim = '	', kwargs...)
```

Send a Tables.jl-compatible object to the clipboard. Default delimiter is tab. Accepts all keyword arguments that can be pased to `CSV.write`.

# Example

```julia-repl
julia> t = (a = [1, 2, 3], b = [100, 200, 300])
(a = [1, 2, 3], b = [100, 200, 300])

julia> cliptable(t)
a   b
1   100
2   200
3   300
```
