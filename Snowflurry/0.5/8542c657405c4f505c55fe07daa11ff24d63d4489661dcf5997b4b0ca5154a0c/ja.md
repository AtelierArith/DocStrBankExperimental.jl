```
CastToPhaseShiftAndHalfRotationXTranspiler,
```

入力回路内のすべての単一量子ゲートを出力回路内の`PhaseShift`と角度π/2の`RotationX`の組み合わせに変換するトランスパイラステージ。入力回路内の任意のゲートに対して、出力内のゲート数はゼロから5の間で変動します。入力回路と出力回路は、任意の状態`Ket`に対して同じ操作を実行します（グローバル位相を除く）。

# フィールド

  * `atol::Real` – 回転角の比較に対する絶対許容誤差（デフォルト = 1e-6）。

# 例

```jldoctest
julia> transpiler = CastToPhaseShiftAndHalfRotationXTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_x(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X──
          
q[2]:─────
          



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z────X_90────Z────X_m90──
                                                 
q[2]:───────────────────────────
                                                 



julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Y──
          
q[2]:─────
          



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──X_90────Z────X_m90──

q[2]:──────────────────────
                                           



julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [universal(1, 0., 0., 0.)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──U(θ=0.0000,ϕ=0.0000,λ=0.0000)──
                                      
q[2]:─────────────────────────────────
                                      



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
     



julia> compare_circuits(circuit, transpiled_circuit)
true

```
