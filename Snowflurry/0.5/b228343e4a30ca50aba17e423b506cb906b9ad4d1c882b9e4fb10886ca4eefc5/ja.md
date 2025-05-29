```
get_num_bits(circuit::QuantumCircuit)::Int
```

`circuit`内の古典ビットの数を返します。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2, bit_count=3);

julia> get_num_bits(c)
3

```
