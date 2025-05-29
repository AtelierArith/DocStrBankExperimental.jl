```
move_instruction(gate::Gate,
    qubit_mapping::AbstractDict{<:Integer,<:Integer})::AbstractGateSymbol
```

`gate`のコピーを返します。`gate`が作用する量子ビットは`qubit_mapping`に基づいて更新されています。

辞書`qubit_mapping`は、ターゲット量子ビットを更新する方法を説明するキーと値のペアを含んでいます。キーは変更するターゲット量子ビットを示し、関連する値は新しい量子ビットを指定します。

# 例

```jldoctest
julia> gate = sigma_x(1)
Gate Object: Snowflurry.SigmaX
Connected_qubits	: [1]
Operator:
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


julia> move_instruction(gate, Dict(1=>2))
Gate Object: Snowflurry.SigmaX
Connected_qubits	: [2]
Operator:
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


```
