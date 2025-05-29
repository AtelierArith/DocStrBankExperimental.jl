```
@mwearray(t)
```

Create a Minimum Working Example (MWE) from a `Vector` or `Matrix` with the same name as the object in the Julia session. Prints to `stdout`.

# Examples

```julia-repl
julia> my_special_matrix = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> @mwearray my_special_matrix
my_special_matrix = """
1,2
3,4
""" |> IOBuffer |> CSV.File |> Tables.matrix
```
