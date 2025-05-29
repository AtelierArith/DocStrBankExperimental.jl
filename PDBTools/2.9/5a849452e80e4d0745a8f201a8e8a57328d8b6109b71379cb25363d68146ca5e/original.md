```
Residue
```

Residue data structure. 

The Residue structure carries the properties of the residue or molecule of the atoms it contains, but it does not copy the original vector of atoms, only the residue meta data for each residue. Thus, changes in the residue atoms will be reflected in the original vector of atoms.

### Example

```jldoctest
julia> using PDBTools

julia> pdb = wget("1LBD");

julia> residues = collect(eachresidue(pdb))
238-element Vector{Residue}[
    SER225A
    ALA226A
    ⋮
    MET461A
    THR462A
]

julia> resnum.(residues[1:3])
3-element Vector{Int32}:
 225
 226
 227

julia> residues[5].chain
"A"

julia> residues[8].range
52:58

julia> mass(residues[1])
82.0385

```
