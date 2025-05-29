```
randdm([rng, T = Float64], d)
```

Generates a density matrix with numeric type `Complex{T}`, of dimension `d` at random.

## Example

```julia
julia> randdm(2)
2×2 Array{Complex{Float64},2}:
 0.477118+0.0im        0.119848-0.0371569im
 0.119848+0.0371569im  0.522882+0.0im      
```
