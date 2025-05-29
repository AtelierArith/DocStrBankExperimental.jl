```
dihedrals(v::AbstractVector{<:AbstractVector}; degrees=true)
```

多くの4つのベクトルのセットに対する二面角を計算します。入力はベクトルのベクトルであり、各要素は4つのベクトルを持つベクトルです。この関数は、ラジアンまたは度での二面角を持つベクトルを返します。

## 例

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing, PDBTools

julia> atoms = read_pdb(Testing.namd2_pdb);

julia> cAs = select(atoms, "name CA and residue < 5");

julia> r1b = select(atoms, "residue 1 and backbone");

julia> ds = dihedrals([ coor(cAs), coor(r1b) ])
2-element Vector{Float32}:
  164.4348
 -115.82544
```
