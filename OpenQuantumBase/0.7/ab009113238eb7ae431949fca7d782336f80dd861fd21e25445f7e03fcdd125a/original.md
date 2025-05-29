```
hamming_weight_operator(num_qubit::Int64, op::String; sp=false)
```

Construct the Hamming weight operator for system of size `num_qubit`. The type of the Hamming weight operator is specified by op: "x", "y" or "z". Generate sparse matrix when `sp` is set to true.

# Examples

```julia-repl
julia> hamming_weight_operator(2,"z")
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  1.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  1.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  2.0+0.0im
```
