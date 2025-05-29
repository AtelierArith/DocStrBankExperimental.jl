```
CastRxToRzAndHalfRotationXTranspiler
```

入力回路内の `RotationX(θ)` ゲートを見つけ、それらを新しい回路内のゲートのシーケンス（`Z90`、`X90`、`PhaseShift(θ)`、`XM90`、および `ZM90`）に変換（キャスト）するトランスパイラーステージ。入力回路と出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler=CastRxToRzAndHalfRotationXTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1,π/8)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(0.3927)──
                   
q[2]:──────────────
                   

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z_90────X_90────P(0.3927)────X_m90────Z_m90──
                                                    
q[2]:───────────────────────────────────────────────
                                                    

julia> compare_circuits(circuit, transpiled_circuit)
true

```
