```
get_num_qubits(circuit::QuantumCircuit)::Int
```

`circuit`内のキュービットの数を返します。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> get_num_qubits(c)
2

```
