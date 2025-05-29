```julia
partial_trace(ρ, qubit_2_keep)

```

Calculate the partial trace of the density matrix `ρ`, assuming all the subsystems are qubits. `qubit_2_keep` denotes the indices whose corresponding qubits are not traced out.

# Examples

```julia-repl
julia> ρ1 = [0.4 0.2; 0.2 0.6]; ρ2 = [0.5 0; 0 0.5];
julia> partial_trace(ρ1⊗ρ2, [1])
2×2 Array{Float64,2}:
 0.4  0.2
 0.2  0.6
```
