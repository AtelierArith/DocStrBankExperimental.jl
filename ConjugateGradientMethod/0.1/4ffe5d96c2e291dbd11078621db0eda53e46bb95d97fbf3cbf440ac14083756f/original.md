```
@cg [1.0] A \ b
```

Solves the least squares problem $\min\|Ax - b\|^2$ using conjugate gradient method.

Between @cg and rdiv call `iterpart` can be specified.

## Examples

```julia-repl
julia> @cg [1 2; 3 4] \ [1, 2]
2-element Array{Float64,1}:
5.551115123125783e-17
0.5000000000000012

julia> @cg 0.5 [1 2; 3 4] \ [1, 2]
2-element Array{Float64,1}:
0.2343820224719101
0.33483146067415726
```

See also [`cg`](@ref) and [`cg!`](@ref).
