```
CastSwapToCZGateTranspiler
```

すべてのスワップゲートを `CZ` ゲートと単一量子ビットゲートに展開するトランスパイラーステージ。入力および出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = CastSwapToCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [swap(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──☒──
       |
q[2]:──☒──

julia> transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:───────────*────Y_m90────────────*────Y_90─────────────*──────────
                |                     |                     |          
q[2]:──Y_m90────Z─────────────Y_90────Z────────────Y_m90────Z────Y_90──
                                              

```
