```
get_pauli(
    circuit::QuantumCircuit;
    imaginary_exponent::Integer=0,
    negative_exponent::Integer=0
)::PauliGroupElement
```

Returns a `PauliGroupElement` given a `circuit` containing Pauli gates.

A Pauli group element corresponds to $i^\delta (-1)^\epsilon \sigma_a$, where $\delta$ and $\epsilon$ are set by specifying `imaginary_exponent` and `negative_exponent`, respectively. The exponents must be 0 or 1. Their default value is 0. As for $\sigma_a$, it is a tensor product of Pauli operators. The Pauli operators are specified in the `circuit`.

# Examples

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 2);

julia> push!(circuit, sigma_x(1), sigma_y(2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────
               
q[2]:───────Y──
               



julia> get_pauli(circuit, imaginary_exponent=1, negative_exponent=1)
Pauli Group Element:
-1.0im*X(1)*Y(2)



```

If multiple Pauli gates are applied to the same qubit in the `circuit`, the gates are multiplied with the first gate in the `circuit` being the rightmost gate in the multiplication.

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 1);

julia> push!(circuit, sigma_x(1), sigma_z(1))
Quantum Circuit Object:
   qubit_count: 1 
   bit_count: 1 
q[1]:──X────Z──
               



julia> get_pauli(circuit)
Pauli Group Element:
1.0im*Y(1)



```
