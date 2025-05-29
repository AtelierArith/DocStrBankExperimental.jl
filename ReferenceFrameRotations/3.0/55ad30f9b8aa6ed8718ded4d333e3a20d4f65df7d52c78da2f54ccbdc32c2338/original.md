```
DCM{T}
```

Direction Cosine Matrix (DCM) of type `T`, which is a 3x3 static matrix of type `T`.

# Examples

```julia-repl
julia> DCM(1.0I)
DCM{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> DCM([1 0 0; 0 -1 0; 0 0 -1])
DCM{Int64}:
 1   0   0
 0  -1   0
 0   0  -1
```
