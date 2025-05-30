```
RejectGatesOnExcludedConnectionsTranspiler
```

除外接続で動作する`Instruction`がある場合に`DomainError`をスローするトランスパイラステージ。除外接続は、特定の`AbstractConnectivity`オブジェクトのパラメータ`excluded_connections`で指定されます。エラーがスローされない場合、関数は同じ`circuit`を返します。

# フィールド

  * connectivity::AbstractConnectivity – `excluded_connections`が指定されている接続性。

# 例

```jldoctest
julia> excluded_positions = Int[];

julia> excluded_connections = [(2, 3)];

julia> connectivity = LineConnectivity(4, excluded_positions, excluded_connections)
LineConnectivity{4}
1──2──3──4
excluded connections: [(2, 3)]


julia> transpiler = RejectGatesOnExcludedConnectionsTranspiler(connectivity);

julia> invalid_circuit = QuantumCircuit(
                      qubit_count = 4,
                      instructions = [sigma_x(4), control_z(3, 2)],
                  )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:──────────
               
q[2]:───────Z──
            |  
q[3]:───────*──
               
q[4]:──X───────
               



julia> transpile(transpiler, invalid_circuit)
ERROR: DomainError with LineConnectivity{4}
1──2──3──4
excluded connections: [(2, 3)]
:
the Gate{Snowflurry.ControlZ} on qubits [3, 2] cannot be applied since connection (2, 3) is unavailable
[...]

julia> valid_circuit = QuantumCircuit(
                      qubit_count = 4,
                      instructions = [sigma_x(1), control_z(3, 4)],
                  )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:──X───────
               
q[2]:──────────
               
q[3]:───────*──
            |  
q[4]:───────Z──
               



julia> transpiled_circuit = transpile(transpiler, valid_circuit)
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:──X───────
               
q[2]:──────────
               
q[3]:───────*──
            |  
q[4]:───────Z──
               


```
