```
write_solutions(filename, solutions)
```

Stores the as a plain text file onto disk. The storage format is as follows. The first line indicates the number of solutions stored followed by a blank line. Then the solutions are stored where each solution is separated by a blank line. Note that the solutions are *always* considered as complex numbers. See [`read_solutions`](@ref) for reading the solution file back.

Note that this is the same file format as used in [Bertini](https://bertini.nd.edu).

## Example

```julia
julia> write_solutions("solutions.txt", [[1, 1], [-1, 2]])

shell> cat solutions.txt
2

1 0
1 0

-1 0
2 0

julia> read_solutions("solutions.txt")
2-element Array{Array{Complex{Int64},1},1}:
 [1 + 0im, 1 + 0im]
 [-1 + 0im, 2 + 0im]
```
