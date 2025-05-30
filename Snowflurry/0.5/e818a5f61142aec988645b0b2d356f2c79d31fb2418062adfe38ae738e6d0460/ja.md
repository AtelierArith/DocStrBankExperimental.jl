```
CompressSingleQubitGatesTranspiler
```

共通のターゲットを持つすべての単一量子ビットゲートを入力回路から集め、それらを新しい回路の単一の `Universal` ゲートに結合するトランスパイラステージ。ゲートの順序は異なる量子ビットに適用される場合に異なる可能性がありますが、入力回路と出力回路は任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = CompressSingleQubitGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_x(1), sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────Y──
               
q[2]:──────────
               



julia> transpiled_circuit=transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──U(θ=0.0000,ϕ=3.1416,λ=0.0000)──
                                      
q[2]:─────────────────────────────────
                                      



julia> compare_circuits(circuit,transpiled_circuit)
true

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(1)
                        sigma_y(1)
                        control_x(2,3)
                        phase_shift(1,π/3)
                    ])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────Y─────────P(1.0472)──
                                 
q[2]:────────────*───────────────
                 |               
q[3]:────────────X───────────────
                                 



julia> transpiled_circuit=transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──U(θ=0.0000,ϕ=-2.0944,λ=0.0000)───────
                                            
q[2]:────────────────────────────────────*──
                                         |  
q[3]:────────────────────────────────────X──
                                            




julia> compare_circuits(circuit,transpiled_circuit)
true

```
