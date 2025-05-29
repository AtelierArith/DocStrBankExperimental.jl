```
mwearray([io::IO=stdout], t::AbstractVector; name=:x)
```

Create a Minimum Working Example (MWE) from a `Vector`. `mwearray` returns the a multi-line string with the code necessary to recreate `t`. Prints to `io`, which is by default `stdout`.

# Example

```julia-repl
julia> mwearray(x; name=:x)
x = """
1
2
3
4
""" |> IOBuffer |> CSV.File |> Tables.matrix |> vec
```
