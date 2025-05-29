```
RejectNonNativeInstructionsTranspiler
```

非ネイティブ`Instruction`が`circuit`内に見つかった場合に`DomainError`をスローするトランスパイラーステージ。エラーがスローされない場合、`circuit`は変更されません。

ネイティブ命令に関する追加情報は[`is_native_instruction`](@ref)を参照してください。

# フィールド

  * connectivity::AbstractConnectivity – 2量子ビットゲートが適用できる接続を指定する接続性。
  * native_gates::Vector{DataType} – ネイティブゲートのリスト。デフォルトでは、Anyon QPUにネイティブなゲートが使用されます。

# 例

```jldoctest
julia> connectivity = LineConnectivity(4)
LineConnectivity{4}
1──2──3──4


julia> default_transpiler = RejectNonNativeInstructionsTranspiler(connectivity);


julia> invalid_circuit = QuantumCircuit(
           qubit_count = 4,
           instructions = [sigma_x(4), control_z(1, 3)],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────|──
            |  
q[3]:───────Z──
               
q[4]:──X───────
               

julia> transpile(default_transpiler, invalid_circuit)
ERROR: DomainError with LineConnectivity{4}
1──2──3──4
[...]


julia> valid_circuit = QuantumCircuit(
           qubit_count = 4,
           instructions = [sigma_x(4), control_z(1, 2)],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────Z──
               
q[3]:──────────
               
q[4]:──X───────
               

julia> transpiled_circuit = transpile(default_transpiler, valid_circuit)
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────Z──
               
q[3]:──────────
               
q[4]:──X───────


julia> custom_circuit = QuantumCircuit(
                  qubit_count = 4,
                  instructions = [control_x(2, 3)],
                  )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:─────
          
q[2]:──*──
       |  
q[3]:──X──
          
q[4]:─────
          

julia> transpile(default_transpiler, custom_circuit)
ERROR: DomainError with LineConnectivity{4}
1──2──3──4
[...]


julia> custom_transpiler = RejectNonNativeInstructionsTranspiler(
            connectivity,
            [Snowflurry.ControlX]
        );


julia> transpiled_circuit = transpile(custom_transpiler, custom_circuit)
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:─────
          
q[2]:──*──
       |  
q[3]:──X──
          
q[4]:─────
          

```
