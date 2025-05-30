```
SimplifyRzGatesTranspiler
```

トランスパイラーステージは、入力回路内の `PhaseShift` ゲートを見つけ、その位相角 phi に基づいて、適切な直角 `RotationZ` ゲート（`SigmaZ`、`Z90`、`ZM90`、`Pi8` または `Pi8Dagger`）にキャストします。`phi≈0.` の場合、ゲートは削除されます。入力回路と出力回路は、任意の状態 `Ket`（グローバル位相を除く）に対して同じ操作を実行します。各ケースで `Base.isapprox()` に使用される許容誤差は、オプションの引数を `Transpiler` に渡すことで設定できます。例: `transpiler=SimplifyRzGatesTranspiler(1.0e-10)`

# フィールド

  * `atol::Real` – 回転角の比較に対する絶対許容誤差（デフォルト = 1e-6）。

# 例

```jldoctest
julia> transpiler = SimplifyRzGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [phase_shift(1, pi/2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(1.5708)──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z_90──
             
q[2]:────────
             

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [phase_shift(1, pi)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(3.1416)──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z──
          
q[2]:─────
          

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [phase_shift(1, 0.)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(0.0000)──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
     



julia> compare_circuits(circuit, transpiled_circuit)
true

```
