```
CastISwapToCZGateTranspiler
```

`ISwap` および `ISwapDagger` ゲートを `CZ` ゲートと単一量子ビットゲートに展開するトランスパイラーステージ。入力および出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = CastISwapToCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [iswap(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──x──
       |
q[2]:──x──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Y_m90─────────────*────Y_90─────────────*────Y_90──────────
                         |                     |                  
q[2]:───────────X_m90────Z────────────X_m90────Z────────────X_90──
                                                                  

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [iswap_dagger(1, 2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──x†──
       |   
q[2]:──x†──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Y_m90─────────────*────Y_m90────────────*────Y_90──────────
                         |                     |                  
q[2]:───────────X_m90────Z─────────────X_90────Z────────────X_90──

```
