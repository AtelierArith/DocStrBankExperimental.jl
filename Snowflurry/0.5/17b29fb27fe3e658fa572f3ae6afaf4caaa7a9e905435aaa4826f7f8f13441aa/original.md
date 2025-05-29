```
simulate(circuit::QuantumCircuit)::Ket
```

Performs an ideal simulation of the `circuit` and returns the final quantum state (i.e. the wave function). The simulator assumes that the initial state $\Psi$ corresponds to the zeroth Fock basis, i.e.: `ψ = fock(0, 2^get_num_qubits(circuit))`. The zeroth Fock basis corresponds to the initial state of most superconducting quantum processors, i.e.:

$$
|\Psi\rangle = |0\rangle^{\otimes n},
$$

where $n$ is the number of qubits.

!!! note
    The input `circuit` must not include `Readout` instructions. Use     [`simulate_shots`](@ref) for the simulation of `circuits` with `Readout`     instructions.


The simulation utilizes the approach described in Listing 5 of [Suzuki *et. al.* (2021)](https://doi.org/10.22331/q-2021-10-06-559).

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H──
          
q[2]:─────
          


julia> push!(c, control_x(1, 2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────*──
            |  
q[2]:───────X──
               


julia> ket = simulate(c)
4-element Ket{ComplexF64}:
0.7071067811865475 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.7071067811865475 + 0.0im


```
