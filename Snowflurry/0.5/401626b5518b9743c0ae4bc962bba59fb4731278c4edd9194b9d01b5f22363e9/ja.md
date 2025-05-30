```
get_num_gates(circuit::QuantumCircuit)::Integer
```

`circuit`内のゲートの数を返します。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1), hadamard(2));

julia> push!(c, control_x(1, 2))
量子回路オブジェクト:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*──
                 |  
q[2]:───────H────X──
                    



julia> get_num_gates(c)
3

```
