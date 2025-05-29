```
mwetable([io::IO=stdout]; name="df")
```

Create a Minimum Working Example (MWE) using the clipboard. `tablmwe` prints out a multi-line comma-separated string and provides the necessary code to read that string using `CSV.File`. The object is assigned the name given by `name` (default `"df"`). Prints to `io`, which is by default `stdout`.

# Examples

```julia-repl
julia> """
       a b
       1 2
       100 200
       """ |> clipboard

julia> mwetable()
df = """
a,b
1,2
100,200
""" |> IOBuffer |> CSV.File
```
