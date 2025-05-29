```
get_measurement_probabilities(
    circuit::QuantumCircuit,
    [target_qubits::Vector{<:Integer}]
)::AbstractVector{<:Real}
```

Returns a list of the measurement probabilities for the `target_qubits` in the `circuit`.

If no `target_qubits` are provided, the probabilities are computed for all the qubits.

The measurement probabilities are listed from the smallest to the largest computational basis state. For instance, for a 2-qubit [`QuantumCircuit`](@ref), the probabilities are listed for $\left|00\right\rangle$, $\left|01\right\rangle$, $\left|10\right\rangle$, and $\left|11\right\rangle$.

!!! note
    By convention, qubit 1 is the leftmost bit, followed by every subsequent qubit.  The notation $\left|10\right\rangle$ indicates that qubit 1 is in state $\left|1\right\rangle$ and qubit 2 in state $\left|0\right\rangle$.


# Examples

The following example constructs a `QuantumCircuit` where the probability of measuring $\left|10\right\rangle$ is 50% and the probability of measuring $\left|11\right\rangle$ is also 50%:

```jldoctest get_circuit_measurement_probabilities
julia> circuit = QuantumCircuit(qubit_count = 2);

julia> push!(circuit, hadamard(1), sigma_x(2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H───────
               
q[2]:───────X──
               



julia> get_measurement_probabilities(circuit)
4-element Vector{Float64}:
 0.0
 0.4999999999999999
 0.0
 0.4999999999999999

```

For the same `circuit`, the probability of measuring qubit 2 and finding 1 is 100%:

```jldoctest get_circuit_measurement_probabilities
julia> target_qubit = [2];

julia> get_measurement_probabilities(circuit, target_qubit)
2-element Vector{Float64}:
 0.0
 0.9999999999999998

```
