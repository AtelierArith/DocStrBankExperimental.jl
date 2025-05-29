```
CastRootZZToZ90AndCZGateTranspiler
```

Transpiler stage which converts all `RootZZ` and `RootZZDagger` gates into `Z90`  (or `ZM90`) gates and a `ControlZ` gate. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

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
