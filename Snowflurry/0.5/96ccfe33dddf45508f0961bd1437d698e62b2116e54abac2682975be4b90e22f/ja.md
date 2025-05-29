```
CastRootZZToZ90AndCZGateTranspiler
```

`RootZZ` および `RootZZDagger` ゲートを `Z90` (または `ZM90`) ゲートと `ControlZ` ゲートに変換するトランスパイラーステージ。入力および出力回路は、任意の状態 `Ket` に対して同じ操作を実行します（グローバル位相を除く）。

# 例

```jldoctest
julia> transpiler = CastRootZZToZ90AndCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [root_zz(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──√ZZ──
        |
q[2]:──√ZZ──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──Z_90────────────*──
                       |
q[2]:──────────Z_90────Z──

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [root_zz_dagger(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──√ZZ†──
        |
q[2]:──√ZZ†──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──Z_m90─────────────*──
                         |
q[2]:───────────Z_m90────Z──
```
