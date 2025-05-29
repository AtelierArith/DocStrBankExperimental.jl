```
write_parameters(filename, parameters)
```

Stores the parameters as a plain text file onto disk. The storage format is as follows. The first line indicates the number of parameter values stored followed by a blank line. Then the parameter values are stored.

See [`read_parameters`](@ref)

Note that this is the same file format as used in [Bertini](https://bertini.nd.edu).

## Example

```julia
julia> write_parameters("parameters.txt", [2.0, -3.2 + 2im])

shell> cat parameters.txt
2

2.0 0.0
-3.2 2.0

julia> read_parameters("parameters.txt")
2-element Array{Complex{Float64},1}:
  2.0 + 0.0im
 -3.2 + 2.0im
```
