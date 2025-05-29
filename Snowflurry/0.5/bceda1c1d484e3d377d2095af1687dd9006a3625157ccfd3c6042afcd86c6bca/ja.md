```
move_instruction(
    original_readout::Readout,
    qubit_mapping::AbstractDict{T,T},
)::AbstractInstruction where {T<:Integer}
```

`original_readout`のコピーを返します。`original_readout`が測定するキュービットは、`qubit_mapping`に基づいて更新されています。

辞書`qubit_mapping`は、ターゲットキュービットを更新する方法を説明するキーと値のペアを含んでいます。キーは変更するターゲットキュービットを示し、関連する値は新しいキュービットを指定します。

# 例

```jldoctest
julia> r = readout(1, 1)
Explicit Readout object:
   connected_qubit: 1 
   destination_bit: 1 

julia> move_instruction(r, Dict(1 => 2))
Explicit Readout object:
   connected_qubit: 2 
   destination_bit: 1 

```
