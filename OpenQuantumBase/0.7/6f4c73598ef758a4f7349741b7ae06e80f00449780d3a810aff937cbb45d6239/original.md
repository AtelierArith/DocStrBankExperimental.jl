```
single_clause(ops::Vector{String}, q_ind, weight, num_qubit; sp=false)
```

Construct a single clause of the multi-qubits Hamiltonian. `ops` is a list of Pauli operator names which appear in this clause. `q_ind` is the list of indices corresponding to the Pauli matrices in `ops`. `weight` is the constant factor of this clause. `num_qubit` is the total number of qubits. A sparse matrix can be construct by setting `sp` to `true`. The following example construct a clause of $Z_1 I Z_3/2$.

# Examples

```julia-repl
julia> single_clause(["z", "z"], [1, 3], 0.5, 3)
8×8 Array{Complex{Float64},2}:
 0.5+0.0im   0.0+0.0im  0.0+0.0im   0.0+0.0im   0.0+0.0im   0.0+0.0im   0.0+0.0im   0.0+0.0im
 0.0+0.0im  -0.5+0.0im  0.0+0.0im  -0.0+0.0im   0.0+0.0im  -0.0+0.0im   0.0+0.0im  -0.0+0.0im
 0.0+0.0im   0.0+0.0im  0.5+0.0im   0.0+0.0im   0.0+0.0im   0.0+0.0im   0.0+0.0im   0.0+0.0im
 0.0+0.0im  -0.0+0.0im  0.0+0.0im  -0.5+0.0im   0.0+0.0im  -0.0+0.0im   0.0+0.0im  -0.0+0.0im
 0.0+0.0im   0.0+0.0im  0.0+0.0im   0.0+0.0im  -0.5+0.0im  -0.0+0.0im  -0.0+0.0im  -0.0+0.0im
 0.0+0.0im  -0.0+0.0im  0.0+0.0im  -0.0+0.0im  -0.0+0.0im   0.5-0.0im  -0.0+0.0im   0.0-0.0im
 0.0+0.0im   0.0+0.0im  0.0+0.0im   0.0+0.0im  -0.0+0.0im  -0.0+0.0im  -0.5+0.0im  -0.0+0.0im
 0.0+0.0im  -0.0+0.0im  0.0+0.0im  -0.0+0.0im  -0.0+0.0im   0.0-0.0im  -0.0+0.0im   0.5-0.0im
```
