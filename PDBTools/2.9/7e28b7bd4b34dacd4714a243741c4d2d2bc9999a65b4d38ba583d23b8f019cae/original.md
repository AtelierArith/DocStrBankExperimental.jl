```
formula(atoms::AbstractVector{<:Atom})
```

Returns the molecular formula of the current selection. The output is an indexable "Formula" structure, where each element is a tuple with the element name and the number of atoms.

## Example

```jldoctest
julia> using PDBTools

julia> pdb  = read_pdb(PDBTools.TESTPDB, "residue 1"); # testing PDB file

julia> resname(pdb[1])
"ALA"

julia> f = formula(pdb)
H₇C₃N₁O₁

julia> f[1]
("H", 7)

```
