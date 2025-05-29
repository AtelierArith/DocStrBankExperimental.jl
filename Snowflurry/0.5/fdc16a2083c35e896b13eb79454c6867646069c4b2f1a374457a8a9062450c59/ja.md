```
CircuitContainsAReadoutTranspiler
```

`QuantumCircuit`に少なくとも1つの`Readout`命令が存在することを保証するトランスパイラーステージです。そうでない場合、エラーがスローされます。このトランスパイラーステージは`QuantumCircuit`を変更しません。

# 例

```jldoctest
julia> transpiler = CircuitContainsAReadoutTranspiler();

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
               

julia> circuit = QuantumCircuit(qubit_count=2, instructions = [hadamard(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H──
          
q[2]:─────
          

julia> transpiled_circuit = transpile(transpiler, circuit)
ERROR: ArgumentError: QuantumCircuit is missing a `Readout`. Would not return any result.
[...]
```
