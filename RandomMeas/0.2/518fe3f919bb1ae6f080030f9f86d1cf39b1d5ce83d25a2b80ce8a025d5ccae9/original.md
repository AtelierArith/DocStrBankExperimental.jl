```
random_circuit(ξ::Vector{Index{Int64}}, depth::Int64)
```

Create a random circuit of the given depth. The function returns a vector of ITensors, each representing a gate in the circuit.

  * If `depth == 0`, a single-qubit random unitary is applied to each site.
  * For `depth > 0`, the circuit is built layer-by-layer:

      * On odd layers, random two-qubit gates are applied on sites 1-2, 3-4, etc.
      * On even layers, random two-qubit gates are applied on sites 2-3, 4-5, etc.

# Arguments

  * `ξ::Vector{Index{Int64}}`: A vector of site indices for the qubits.
  * `depth::Int64`: The depth of the circuit (non-negative integer).

# Returns

A vector of ITensors representing the random circuit gates.

# Example

```julia
circuit = random_circuit(siteinds("Qubit", 10), 3)
```
