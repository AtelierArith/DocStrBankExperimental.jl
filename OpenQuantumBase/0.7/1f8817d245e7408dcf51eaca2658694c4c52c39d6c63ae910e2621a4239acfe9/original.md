```
local_field_term(h, idx, num_qubit; sp=false)
```

Construct local Hamiltonian of the form $∑hᵢσᵢᶻ$. `idx` is the index of all local field terms and `h` is a list of the corresponding weights. `num_qubit` is the total number of qubits. Generate sparse matrix when `sp` is set to true.

# Examples

```julia-repl
julia> local_field_term([1.0, 0.5], [1, 2], 2) == σz⊗σi+0.5σi⊗σz
true
```
