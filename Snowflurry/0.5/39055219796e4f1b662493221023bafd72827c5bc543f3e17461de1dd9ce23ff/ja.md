```
CompressRzGatesTranspiler
```

入力回路内で共通のターゲットを持つすべてのRz型ゲートを集め、それらを新しい回路内の単一のPhaseShiftゲートに結合するトランスパイラステージです。ゲートの順序は異なる量子ビットに適用される場合に異なる可能性がありますが、入力回路と出力回路は任意の状態`Ket`に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = CompressRzGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_z(1), z_90(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z────Z_90──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(-1.5708)──
                   
q[2]:──────────────
                   

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [sigma_z(1), pi_8(1), control_x(2,3), z_minus_90(1)]
                )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──Z────T─────────Z_m90──
                             
q[2]:────────────*───────────
                 |           
q[3]:────────────X───────────
                             

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──P(2.3562)───────
                       
q[2]:───────────────*──
                    |  
q[3]:───────────────X──
                       

julia> compare_circuits(circuit, transpiled_circuit)
true

```
