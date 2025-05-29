```
cg!(x, A, b, [iterpart=1.0])
cg!(x, A, b, [iternum=size(A,1)])
```

Solves the least squares problem $\min\|Ax - b\|^2$ using conjugate gradient method. `x` is used as an initial value and is replaced with the result.

`iternum` specifies the number of iterations to stop after (minimum 1).

## Examples

```julia-repl
julia> x = zeros(2);

julia> cg!(x, [1 2; 3 4], [1, 2])
2-element Array{Float64,1}:
5.551115123125783e-17
0.5000000000000012
```

See also [`cg`](@ref) and [`@cg`](@ref).
