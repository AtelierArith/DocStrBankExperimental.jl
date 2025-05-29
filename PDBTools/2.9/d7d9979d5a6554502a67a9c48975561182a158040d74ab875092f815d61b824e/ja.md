```
moveto!(atoms::AbstractVector{<:Atom}; center::AbstractVector{<:Real}=SVector(0.0, 0.0, 0.0))
```

原子の質量中心を指定された `center` 位置に移動します。デフォルトでは原点に移動します。

# 例

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.SMALLPDB);

julia> center_of_mass(atoms)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
  -5.584422772707132
 -13.110413081059928
  -7.139970851058855

julia> moveto!(atoms; center = [1.0, 2.0, 3.0]);

julia> center_of_mass(atoms)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 1.0000000263619948
 1.9999999934852166
 2.9999999509668918
```
