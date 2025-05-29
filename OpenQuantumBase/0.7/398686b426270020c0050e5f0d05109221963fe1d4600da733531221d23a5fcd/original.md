```
two_local_term(j, idx, num_qubit; sp=false)
```

Construct local Hamiltonian of the form $∑Jᵢⱼσᵢᶻσⱼᶻ$. `idx` is the index of all two local terms and `j` is a list of the corresponding weights. `num_qubit` is the total number of qubits. Generate sparse matrix when `sp` is set to true.

# Examples

```julia-repl
julia> two_local_term([1.0, 0.5], [[1,2], [1,3]], 3) == σz⊗σz⊗σi + 0.5σz⊗σi⊗σz
true
```
