```
ReadoutsAreFinalInstructionsTranspiler
```

各 `Readout` 命令が読み出しが存在する各量子ビットの最後の操作であることを保証するトランスパイラーステージです。また、同じ量子ビットに対して繰り返しの読み出しが発生しないことも確認します。これらの検証に失敗した場合はエラーがスローされます。このトランスパイラーステージは `QuantumCircuit` を変更しません。

# 例

```jldoctest
julia> transpiler = ReadoutsAreFinalInstructionsTranspiler();

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [hadamard(1), readout(1,1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────✲──
               
q[2]:──────────
               

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────✲──
               
q[2]:──────────
               

julia> circuit = QuantumCircuit(
                    qubit_count=2,
                    instructions = [hadamard(1), readout(1,1), sigma_x(1)]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────✲────X──
                    
q[2]:───────────────
                    

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: AssertionError: Cannot perform `Gate` following `Readout` on qubit: 1
[...]

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [readout(1,1), readout(1,2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──✲────✲──
               
q[2]:──────────
               

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: AssertionError: Found multiple `Readouts` on qubit: 1
[...]
```
