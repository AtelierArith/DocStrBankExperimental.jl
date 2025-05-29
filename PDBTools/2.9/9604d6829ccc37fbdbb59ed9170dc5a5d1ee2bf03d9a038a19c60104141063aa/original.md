```
stoichiometry(atoms::AbstractVector{<:Atom})
```

Returns the stoichiometry of atom selection in a `Formula` structure. 

### Example

```jldoctest
julia> using PDBTools

julia> pdb  = read_pdb(PDBTools.TESTPDB, "water"); # testing PDB file

julia> stoichiometry(pdb)
H₂O₁
```
