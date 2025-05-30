```
RemoveSwapBySwappingGatesTranspiler
```

`circuit` から `Swap` ゲートを削除するトランスパイラーステージで、全ての接続性を前提としています。

!!! warning "初期状態は基底状態でなければなりません！"
    このトランスパイラーステージは、入力状態が $|0\rangle^{\otimes N}$ であると仮定しています。ここで、$N$ はキュービットの数です。このステージは、入力状態が $|0\rangle^{\otimes N}$ でないサブ回路には使用すべきではありません。


このトランスパイラーステージは、各 `Swap` ゲートの前にあるゲートを移動させることによって `Swap` ゲートを排除します。

# 例

```jldoctest
julia> transpiler = RemoveSwapBySwappingGatesTranspiler();

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [hadamard(1), swap(1, 2), sigma_x(2)]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────☒───────
            |       
q[2]:───────☒────X──
                    



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──────────
               
q[2]:──H────X──
               



```
