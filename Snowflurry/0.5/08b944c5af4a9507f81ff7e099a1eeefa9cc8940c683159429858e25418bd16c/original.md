```
get_imaginary_exponent(pauli::PauliGroupElement)::Int
```

Returns the imaginary exponent of a `PauliGroupElement`.

# Examples

```jldoctest
julia> gate = sigma_x(2);

julia> num_qubits = 3;

julia> pauli = get_pauli(gate, num_qubits, imaginary_exponent = 1)
Pauli Group Element:
1.0im*X(2)



julia> get_imaginary_exponent(pauli)
1

```
