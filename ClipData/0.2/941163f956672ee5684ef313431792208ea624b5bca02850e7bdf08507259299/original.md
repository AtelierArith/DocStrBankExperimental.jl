```
@mwetable(t)
```

Create a Minimum Working Example (MWE) from an existing Tables.jl-compatible object. `tablmwe` prints out a multi-line comma-separated string and provides the necessary code to read that string using `CSV.File`. The name assigned to the object in the MWE is the same as the name of the input object. Prints to `stdout`.

# Examples

```julia-repl
julia> my_special_table = (a = [1, 2, 3], b = [100, 200, 300])
(a = [1, 2, 3], b = [100, 200, 300])

julia> @mwetable my_special_table
my_special_table = """
a,b
1,100
2,200
3,300
""" |> IOBuffer |> CSV.File
```
