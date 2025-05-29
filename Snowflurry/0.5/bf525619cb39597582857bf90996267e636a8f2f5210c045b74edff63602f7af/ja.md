```
SequentialTranspiler(Vector{<:Transpiler})
```

配列の `Transpiler` ステージから構築される複合トランスパイラオブジェクト。 `transpile(::SequentialTranspiler,::QuantumCircuit)` を呼び出すと、入力回路に対して各ステージが順番に適用され、トランスパイルされた出力回路が返されます。入力回路と出力回路は、任意の状態 `Ket` に対して同じ操作を行います（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = SequentialTranspiler([
                        CompressSingleQubitGatesTranspiler(),
                        CastToPhaseShiftAndHalfRotationXTranspiler()
                    ]);

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_x(1), hadamard(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────H──
               
q[2]:──────────
               



julia> transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z────X_90────Z_90────X_m90────Z──
                                                              
q[2]:───────────────────────────────────
                                                              



julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(1),
                        sigma_y(1),
                        control_x(2,3),
                        phase_shift(1,π/3)
                    ])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────Y─────────P(1.0472)──

q[2]:────────────*───────────────
                 |               
q[3]:────────────X───────────────
                                 



julia> transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──P(-2.0944)───────
                        
q[2]:────────────────*──
                     |  
q[3]:────────────────X──
                        



```
