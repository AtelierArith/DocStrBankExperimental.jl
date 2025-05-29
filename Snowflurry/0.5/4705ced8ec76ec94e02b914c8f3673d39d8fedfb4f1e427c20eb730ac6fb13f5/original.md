```
get_negative_exponent(pauli::PauliGroupElement)::Int
```

Returns the negative exponent of a `PauliGroupElement`.

# Examples

```jldoctest
julia> gate = sigma_x(2);

julia> num_qubits = 3;

julia> pauli = get_pauli(gate, num_qubits, negative_exponent = 1)
Pauli Group Element:
-1.0*X(2)



julia> get_negative_exponent(pauli)
1

```
