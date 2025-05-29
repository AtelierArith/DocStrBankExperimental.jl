```
is_native_circuit(
    circuit::QuantumCircuit,
    connectivity::GeometricConnectivity,
    native_gates::Vector{DataType} = set_of_native_gates,
)::Tuple{Bool,String}
```

`circuit`が`connectivity`および可能な`native_gates`のリストに対してネイティブ命令のみを含む場合、`(true, "")`を返します。それ以外の場合は`(false, "error_message")`を返します。Anyon QPUのネイティブゲートはデフォルトで使用されます。

ネイティブ命令の識別に関する詳細は、[`is_native_instruction`](@ref)を参照してください。

# 例

```jldoctest is_native_instruction
julia> connectivity = LineConnectivity(3)
LineConnectivity{3}
1──2──3


julia> native_circuit = QuantumCircuit(
           qubit_count = 3,
           instructions = [sigma_x(1), control_z(2, 3)]
       )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X───────
               
q[2]:───────*──
            |  
q[3]:───────Z──
               

julia> is_native_circuit(native_circuit, connectivity)
(true, "")

julia> foreign_circuit = QuantumCircuit(
                  qubit_count = 3,
                  instructions = [sigma_x(1), control_x(2, 3)]
              )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X───────
               
q[2]:───────*──
            |  
q[3]:───────X──
               

julia> is_native_circuit(foreign_circuit, connectivity)
(false, "Instruction type Gate{Snowflurry.ControlX} with targets [2, 3] is not native on the connectivity")

julia> is_native_circuit(
            foreign_circuit,
            connectivity,
            [Snowflurry.ControlX, Snowflurry.SigmaX]
        )
(true, "")

```

次の回路は、Toffoliゲートが2つ以上の量子ビットに適用されているため、ネイティブではありません：

```jldoctest is_native_instruction
julia> foreign_circuit = QuantumCircuit(
           qubit_count = 3,
           instructions = [sigma_x(1), toffoli(1, 2, 3)]
       )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────*──
            |  
q[2]:───────*──
            |  
q[3]:───────X──
               

julia> is_native_circuit(
            foreign_circuit,
            connectivity,
            [Snowflurry.Toffoli, Snowflurry.SigmaX]
        )
(false, "Instruction type Gate{Snowflurry.Toffoli} with targets [1, 2, 3] is not native on the connectivity")

```
