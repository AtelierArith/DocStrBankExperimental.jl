```
QuantumCircuit(
    qubit_count::Int,
    bit_count::Int,
    instructions::Vector{AbstractInstruction},
    name::String = "default"
)
QuantumCircuit(circuit::QuantumCircuit)
```

*量子回路*を記述するデータ構造。

# フィールド

  * `qubit_count::Int` – 最大の量子ビットインデックス（例：`qubit_count=n`を指定すると、量子ビット1からnを使用可能）。
  * `bit_count::Int` – オプション：古典ビットの数（すなわち、結果レジスタのサイズ）。指定しない場合は`qubit_count`がデフォルト。
  * `instructions::Vector{AbstractInstruction}` – オプション：量子ビットに作用する`AbstractInstructions`（`Gates`および`Readouts`）のシーケンス。デフォルトは空のベクター。
  * `name::String` – オプション：回路および対応するジョブの名前。ハードウェアまたは仮想QPUに送信される際にジョブを識別するために使用される。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
```

`QuantumCircuit`は[`Gate`](@ref Gate)および[`Readout`](@ref Readout)構造体で初期化できます：

```jldoctest circuit
julia> c = QuantumCircuit(
            qubit_count = 2,
            instructions = [
                hadamard(1),
                sigma_x(2),
                control_x(1, 2),
                readout(1, 1),
                readout(2, 2)
            ])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*────✲───────
                 |            
q[2]:───────X────X─────────✲──
                              
```

`QuantumCircuit`のディープコピーは、次の関数で取得できます：

```jldoctest circuit
julia> c_copy = QuantumCircuit(c)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*────✲───────
                 |            
q[2]:───────X────X─────────✲──
                              
```
