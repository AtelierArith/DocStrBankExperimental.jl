```
compare_circuits(c0::QuantumCircuit, c1::QuantumCircuit)::Bool
```

任意の入力状態（`Ket`）に対する効果に基づいて、2つの[`QuantumCircuit`](@ref)オブジェクトの同等性をテストします。回路は、任意の入力に対して同じ出力を生成する場合、グローバル位相を除いて同等です。異なる順序で異なるターゲットに適用されるゲートを持つ回路も同等である可能性があります。

!!! note
    いずれかの`QuantumCircuit`に`Readout`命令が存在する場合、`compare_circuits`は両方の回路が同じ量子ビットをターゲットにした読み出しを持ち、読み出し後にそれらの量子ビット上に操作が存在しないことを確認します。


# 例

```jldoctest
julia> c0 = QuantumCircuit(qubit_count = 1, instructions = [sigma_x(1), sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 1 
   bit_count: 1 
q[1]:──X────Y──
               



julia> c1 = QuantumCircuit(qubit_count = 1, instructions = [phase_shift(1, π)])
Quantum Circuit Object:
   qubit_count: 1  
   bit_count: 1  
q[1]:──P(3.1416)──
                  



julia> compare_circuits(c0, c1)
true            

julia> c0 = QuantumCircuit(
                qubit_count = 3,
                instructions = [sigma_x(1), sigma_y(1), control_x(2, 3)]
            )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────Y───────
                    
q[2]:────────────*──
                 |  
q[3]:────────────X──
                    



julia> c1 = QuantumCircuit(
                qubit_count = 3,
                instructions = [control_x(2, 3), sigma_x(1), sigma_y(1)]
            )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:───────X────Y──
                    
q[2]:──*────────────
       |            
q[3]:──X────────────
                    



julia> compare_circuits(c0, c1)
true    

julia> c2 = QuantumCircuit(qubit_count = 3, instructions = [sigma_x(1), readout(1, 1)])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────✲──
               
q[2]:──────────
               
q[3]:──────────
               
julia> c3 = QuantumCircuit(qubit_count = 3, instructions = [sigma_x(1)])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X──
          
q[2]:─────
          
q[3]:─────
          

julia> compare_circuits(c2,c3)
false    

```
