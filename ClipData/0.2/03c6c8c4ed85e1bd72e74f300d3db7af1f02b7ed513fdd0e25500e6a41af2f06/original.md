```
mwetable([io::IO=stdout], t; name="df")
```

Create a Minimum Working Example (MWE) from an existing Tables.jl-compatible object. `tablmwe` prints out a multi-line comma-separated string and provides the necessary code to read that string using `CSV.File`. The object is assigned the name given by `name` (default `:df`). Prints to `io`, which is by default `stdout`.

# Examples

```julia-repl
julia> t = (a = [1, 2, 3], b = [100, 200, 300])
(a = [1, 2, 3], b = [100, 200, 300])

julia> mwetable(t)
df = """
a,b
1,100
2,200
3,300
""" |> IOBuffer |> CSV.File
```
