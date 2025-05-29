```
random_Pauli_layer(ξ::Vector{Index{Int64}}, p::Vector{Float64})
```

Construct a layer of random single-qubit Pauli operations to simulate local depolarization. Upon avereraging, this corresponds to the local depolarization channel with strength p.

For each qubit (with index i), a random Pauli operation is applied with the following probabilities:

  * With probability 1 - 3p_i/4: No operation is applied (the qubit remains unchanged).
  * With probability p_i/4} each: Apply the X, Y, or Z gate.

Here, p_i is the depolarization probability for qubit i.

# Arguments

  * `ξ::Vector{Index{Int64}}`: A vector of ITensor indices representing the qubit sites.
  * `p::Vector{Float64}`: A vector of depolarization probabilities (one per qubit).

# Returns

A vector of ITensors representing the applied Pauli gates. If no gate is applied on a site (with probability 1 - 3p_i/4, that site is omitted from the returned circuit.

# Example

```julia
circuit = random_Pauli_layer(siteinds("Qubit", 5), 0.05 * ones(5))
```
