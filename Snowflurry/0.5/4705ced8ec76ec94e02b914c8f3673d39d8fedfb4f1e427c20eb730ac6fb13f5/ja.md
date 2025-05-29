```
get_negative_exponent(pauli::PauliGroupElement)::Int
```

`PauliGroupElement`の負の指数を返します。

# 例

```jldoctest
julia> gate = sigma_x(2);

julia> num_qubits = 3;

julia> pauli = get_pauli(gate, num_qubits, negative_exponent = 1)
Pauli Group Element:
-1.0*X(2)



julia> get_negative_exponent(pauli)
1

```
