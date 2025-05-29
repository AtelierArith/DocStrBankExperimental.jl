```
UnsupportedGatesTranspiler
```

2つ以上の量子ビットで動作する`Controlled`ゲートが見つかった場合に`NotImplementedError`をスローするトランスパイラステージです。

# 例

```jldoctest
julia> transpiler = UnsupportedGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [control_z(1, 2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──*──
       |  
q[2]:──Z──
          

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──*──
       |  
q[2]:──Z──
          

julia> invalid_circuit = QuantumCircuit(
               qubit_count = 4,
               instructions = [controlled(hadamard(2), [1, 3])],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:──*──
       |  
q[2]:──H──
       |  
q[3]:──*──
          
q[4]:─────
          

julia> transpiled_circuit = transpile(transpiler, invalid_circuit)
ERROR: NotImplementedError{Gate{Controlled{Snowflurry.Hadamard}}}(:Transpiler, Gate Object: Controlled{Snowflurry.Hadamard}
[...]
```
