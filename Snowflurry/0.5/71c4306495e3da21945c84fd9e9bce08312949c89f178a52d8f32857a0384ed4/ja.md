```
simulate_shots(c::QuantumCircuit, shots_count::Int = 100)
```

与えられたショット数で回路を実行することによって量子コンピュータをエミュレートし、回路内に存在する`Readout`命令によって規定された測定結果を返します。 測定された状態の分布は、結果の状態Ketの係数に依存します。

# 例

```jldoctest simulate_shots; filter = r"00|11"
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1), control_x(1, 2), readout(1, 1), readout(2, 2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────*────✲───────
            |            
q[2]:───────X─────────✲──


julia> simulate_shots(c, 99)
99-element Vector{String}:
 "11"
 "00"
 "11"
 "11"
 "11"
 "11"
 "11"
 "00"
 "00"
 "11"
 ⋮
 "00"
 "00"
 "11"
 "00"
 "00"
 "00"
 "00"
 "00"
 "00"
```
