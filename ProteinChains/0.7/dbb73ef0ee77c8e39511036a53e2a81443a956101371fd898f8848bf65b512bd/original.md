```
ProteinStructureStore <: AbstractDict{InlineStrings.String31,ProteinStructure}
```

A JLD2-based store for protein structures implementing the `AbstractDict` interface, allowing for dictionary operations on the stored structures.

Keys are stored as `InlineStrings.String31` objects to reduce references. This means keys are limited to 31 bytes.

A `ProteinStructureStore` gets closed automatically when there no longer exists a program-accessible reference to it.

## Examples

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
