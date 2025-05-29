```
center_of_mass(atoms::AbstractVector{<:Atom})
```

原子の重心を計算します。

# 例

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.SMALLPDB);

julia> center_of_mass(atoms)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
  -5.584422772707132
 -13.110413081059928
  -7.139970851058855
```
