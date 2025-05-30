```
SimplifyTrivialGatesTranspiler
```

効果のないゲート（例：`Identity`）や、パラメータがnullのパラメータ化ゲート（例：`rotation_x(target, 0.)`）を削除するトランスパイラーステージ。入力および出力回路は、任意の状態`Ket`に対して同じ操作を実行します（グローバル位相を除く）。各ケースで`Base.isapprox()`に使用される許容誤差は、トランスパイラーにオプション引数を渡すことで設定できます（例：`transpiler=SimplifyTrivialGatesTranspiler(1.0e-10)`）。

# フィールド

  * `atol::Real` – 回転角の比較に対する絶対許容誤差（デフォルト = 1e-6）。

# 例

```jldoctest
julia> transpiler = SimplifyTrivialGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [identity_gate(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──I──
          
q[2]:─────
          
julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:      

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
