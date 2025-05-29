```
SwapQubitsForAdjacencyTranspiler
```

隣接する量子ビットに作用する最終的な `Operator` を実現するために、マルチキュービットゲートの周りに `Swap` ゲートを追加するトランスパイラーステージです。入力および出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# フィールド

  * `connectivity::AbstractConnectivity` – `Swap` ゲートの配置のための接続性。

# 例

```jldoctest
julia> transpiler = SwapQubitsForAdjacencyTranspiler(LineConnectivity(6));

julia> circuit = QuantumCircuit(qubit_count = 6, instructions = [toffoli(4, 6, 1)])
Quantum Circuit Object:
   qubit_count: 6 
   bit_count: 6 
q[1]:──X──
       |  
q[2]:──|──
       |  
q[3]:──|──
       |  
q[4]:──*──
       |  
q[5]:──|──
       |  
q[6]:──*──
          




julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 6 
   bit_count: 6 
q[1]:───────────────────────────X───────────────────────────
                                |                           
q[2]:───────☒───────────────────*───────────────────☒───────
            |                   |                   |       
q[3]:──☒────☒──────────────☒────*────☒──────────────☒────☒──
       |                   |         |                   |  
q[4]:──☒──────────────☒────☒─────────☒────☒──────────────☒──
                      |                   |                 
q[5]:────────────☒────☒───────────────────☒────☒────────────
                 |                             |            
q[6]:────────────☒─────────────────────────────☒────────────
                                                            



julia> compare_circuits(circuit, transpiled_circuit)
true

```
