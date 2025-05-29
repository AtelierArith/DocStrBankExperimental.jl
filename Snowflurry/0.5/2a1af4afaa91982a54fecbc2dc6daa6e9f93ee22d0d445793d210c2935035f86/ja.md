```
SimplifyRxGatesTranspiler
```

入力回路内の `RotationX` ゲートを見つけ、その角度 theta に基づいて、適切な直角 `RotationX` ゲート（`SigmaX`、`X90`、または `XM90`）に変換するトランスパイラーステージです。`theta≈0.` の場合、ゲートは削除されます。入力回路と出力回路は、任意の状態 `Ket` に対して同じ操作を行います（グローバル位相を除く）。

# フィールド

  * `atol::Real` – 回転角の比較に対する絶対許容誤差（デフォルト = 1e-6）。

# 例

```jldoctest
julia> transpiler = SimplifyRxGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1, pi/2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(1.5708)──
                   
q[2]:──────────────
                   

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X_90──
             
q[2]:────────
             

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1, pi)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(3.1416)──
                   
q[2]:──────────────
                   


julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X──
          
q[2]:─────
          

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1, 0.)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(0.0000)──
                   
q[2]:──────────────
                   


julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
     



julia> compare_circuits(circuit, transpiled_circuit)
true

```
