```
cg(A, b, [iterpart=1.0])
cg(A, b, [iternum=size(A,1)])
```

Solves the least squares problem $\min\|Ax - b\|^2$ using conjugate gradient method. To use initial value see `cg!`.

`iternum` specifies the number of iterations to stop after (minimum 1). `iterpart` = `iternum` / $size(A,1)$

## Examples

```julia-repl
julia> cg([1 2; 3 4], [1, 2])
2-element Array{Float64,1}:
5.551115123125783e-17
0.5000000000000012
```

See also [`cg!`](@ref) and [`@cg`](@ref).
