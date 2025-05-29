```
DecomposeSingleTargetSingleControlGatesTranspiler
```

入力回路内の単一制御、単一ターゲットの `Controlled` ゲートを見つけ、それを新しい同等の回路内の `RotationZ` (Rz)、`ControlX`、`Universal` (U)、および `PhaseShift` (P) ゲートのシーケンスに変換するトランスパイラーステージ。参考文献として、Nielsen と Chuang の "Quantum Computation and Quantum Information" の p. 180 を参照してください。入力回路と出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

!!! note
    `Controlled` ゲートのカーネルによってターゲットキュービットに適用されるグローバル位相がある場合、この分解はそれを保持します。


例えば、`rotation_z(pi)` と `phase_shift(pi)` のカーネルは位相オフセットを持つ結果を生成します。

# 例

```jldoctest
julia> transpiler = DecomposeSingleTargetSingleControlGatesTranspiler();

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [sigma_x(1), controlled(rotation_z(2, pi), [1])]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────────*───────
                |       
q[2]:───────Rz(3.1416)──
                        
julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────────────────*──────────────────────────────────────*───────────────────────────────────
                           |                                      |                                   
q[2]:───────Rz(-1.5708)────X────U(θ=0.0000,ϕ=-1.5708,λ=0.0000)────X────U(θ=0.0000,ϕ=3.1416,λ=0.0000)──
                                                                                                      
julia> compare_circuits(circuit, transpiled_circuit)
true

julia> simulate(transpiled_circuit)
4-element Ket{ComplexF64}:
0.0 + 0.0im
-0.0 + 0.0im
0.7071067811865477 - 0.7071067811865474im
0.0 + 0.0im

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [sigma_x(1), controlled(phase_shift(2, pi), [1])]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────────*──────
                |      
q[2]:───────P(3.1416)──
                       

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────────────────*──────────────────────────────────────*─────────────────────────────────────P(1.5708)──
                           |                                      |                                                
q[2]:───────Rz(-1.5708)────X────U(θ=0.0000,ϕ=-1.5708,λ=0.0000)────X────U(θ=0.0000,ϕ=3.1416,λ=0.0000)───────────────
                                                                                                                   

julia> compare_circuits(circuit,transpiled_circuit)
true

julia> simulate(circuit)
4-element Ket{ComplexF64}:
0.0 + 0.0im
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im

```
