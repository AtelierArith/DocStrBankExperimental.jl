```
dihedrals(v::AbstractVector{<:AbstractVector}; degrees=true)
```

Computes the dihedral angles for many sets of 4 vectors. The input is a vector of vectors, where each element is a vector with 4 vectors. The function returns a vector with the dihedral angles in radians or degrees.

## Example

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
