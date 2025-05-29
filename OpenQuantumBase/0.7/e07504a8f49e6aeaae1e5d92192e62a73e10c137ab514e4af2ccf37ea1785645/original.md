```
collective_operator(op, num_qubit; sp=false)
```

Construct the collective operator for a system of `num_qubit` qubits. `op` is the name of the collective Pauli matrix. For example, the following code construct an $IZ + ZI$ matrix. Generate sparse matrix when `sp` is set to true.

# Examples

```julia-repl
julia> collective_operator("z", 2)
4×4 Array{Complex{Float64},2}:
 2.0+0.0im  0.0+0.0im  0.0+0.0im   0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im   0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im   0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  -2.0+0.0im
```
