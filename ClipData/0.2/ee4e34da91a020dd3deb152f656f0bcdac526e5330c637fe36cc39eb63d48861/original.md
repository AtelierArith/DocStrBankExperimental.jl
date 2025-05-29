```
mwearray([io::IO=stdout]; name=:X)
```

Create a Minimum Working Example (MWE) from the clipboard to create an array. `mwearray` returns the a multi-line string with the code necessary to read the string stored in clipboard as a `Vector` or `Matrix`. Prints to `io`, which is by default `stdout`.

# Examples

```julia-repl
julia> """
       1 2
       3 4
       """ |> clipboard

julia> mwearray()
X = """
1,2
3,4
""" |> IOBuffer |> CSV.File |> Tables.matrix
```
