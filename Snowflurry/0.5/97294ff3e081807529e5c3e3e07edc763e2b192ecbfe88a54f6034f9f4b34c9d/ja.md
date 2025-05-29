```
CastToffoliToCXGateTranspiler
```

すべてのトフォリゲートを `CX` ゲートと単一量子ビットゲートに展開するトランスパイラーステージ。入力および出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = CastToffoliToCXGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 3, instructions = [toffoli(1, 2, 3)])
Quantum Circuit Object:
   qubit_count: 3
   bit_count: 3
q[1]:──*──
       |
q[2]:──*──
       |
q[3]:──X──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──────────────────*────────────────────*──────────────*─────────T──────────*──
                       |                    |              |                    |  
q[2]:───────*──────────|─────────*──────────|────T─────────X──────────────T†────X──
            |          |         |          |                                      
q[3]:──H────X────T†────X────T────X────T†────X─────────T─────────H──────────────────
```
