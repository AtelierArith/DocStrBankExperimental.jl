```
read_parameters(filename)
```

Read the parameters stored with [`write_parameters`](@ref).

## Example

```julia
julia> write_parameters("parameters.txt", [2.0, -3.2 + 2im])

julia> read_parameters("parameters.txt")
2-element Array{Complex{Float64},1}:
  2.0 + 0.0im
 -3.2 + 2.0im
```
