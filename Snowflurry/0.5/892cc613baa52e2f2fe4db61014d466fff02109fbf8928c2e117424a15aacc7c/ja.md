```
get_name(circuit::QuantumCircuit)::String
```

`circuit`の名前と対応するジョブを返します。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2, name = "my_circuit");

julia> get_name(c)
"my_circuit"

```
