```
mwearray([io::IO=stdout], t::AbstractMatrix; name=:X)
```

Create a Minimum Working Example (MWE) from a `Matrix`. `mwearray` returns the a multi-line string with the code necessary to recreate `t`. Prints to `io`, which is by default `stdout`.

# Examples

```julia-repl
julia> X = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mwearray(X)
X = """
1,2
3,4
""" |> IOBuffer |> CSV.File |> Tables.matrix
```
