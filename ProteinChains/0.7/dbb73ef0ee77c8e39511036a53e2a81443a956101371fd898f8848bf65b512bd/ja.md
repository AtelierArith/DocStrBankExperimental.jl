```
ProteinStructureStore <: AbstractDict{InlineStrings.String31,ProteinStructure}
```

`AbstractDict` インターフェースを実装した JLD2 ベースのタンパク質構造ストアで、保存された構造に対して辞書操作を可能にします。

キーは参照を減らすために `InlineStrings.String31` オブジェクトとして保存されます。これは、キーが 31 バイトに制限されることを意味します。

`ProteinStructureStore` は、プログラムからアクセス可能な参照がもはや存在しないときに自動的に閉じられます。

## 例

```jldoctest
julia> store = ProteinStructureStore("store.pss")
ProteinStructureStore with 0 entries

julia> store["3HFM"] = pdb"3HFM"
[ Info: Downloading file from PDB: 3HFM
3-element ProteinStructure "3HFM.cif":
 215-residue ProteinChain{Float64} (H)
 214-residue ProteinChain{Float64} (L)
 129-residue ProteinChain{Float64} (Y)

julia> store
ProteinStructureStore with 1 entry

julia> keys(store)
Set{InlineStrings.String31} with 1 element:
  InlineStrings.String31("3HFM")

julia> delete!(store, "3HFM")
ProteinStructureStore with 0 entries
```
