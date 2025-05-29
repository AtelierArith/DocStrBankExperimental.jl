```
get_pauli(
    gate::AbstractGateSymbol,
    num_qubits::Integer;
    imaginary_exponent::Integer=0,
    negative_exponent::Integer=0
)::PauliGroupElement
```

Returns a `PauliGroupElement` given a `gate` and the number of qubits.

A Pauli group element corresponds to $i^\delta (-1)^\epsilon \sigma_a$, where $\delta$ and $\epsilon$ are set by specifying `imaginary_exponent` and `negative_exponent`, respectively. The exponents must be 0 or 1. Their default value is 0. As for $\sigma_a$, it is a tensor product of Pauli operators. In this variant of the `get_pauli` function, a single Pauli operator is set by providing a `gate`. The number of qubits is specified by `num_qubits`.

# Examples

```jldoctest
julia> gate = sigma_x(2);

julia> num_qubits = 3;

julia> get_pauli(gate, num_qubits)
Pauli Group Element:
1.0*X(2)



```
