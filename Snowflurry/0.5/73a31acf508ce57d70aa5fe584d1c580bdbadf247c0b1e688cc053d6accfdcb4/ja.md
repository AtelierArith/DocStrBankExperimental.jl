```
get_num_gates_per_type(
    circuit::QuantumCircuit
)::AbstractDict{<: AbstractString, <:Integer}
```

`circuit`内に見つかった各タイプのゲートの数をリストする辞書を返します。

辞書のキーはゲートの命令シンボルで、値は見つかったゲートの数です。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1), hadamard(2));

julia> push!(c, control_x(1, 2));

julia> push!(c, hadamard(2))
量子回路オブジェクト:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*───────
                 |       
q[2]:───────H────X────H──
                         



julia> get_num_gates_per_type(c)
Dict{String, Int64} with 2 entries:
  "h"  => 3
  "cx" => 1

```
