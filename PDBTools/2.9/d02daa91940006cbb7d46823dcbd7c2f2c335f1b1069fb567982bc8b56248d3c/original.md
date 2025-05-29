```
eachresidue(atoms::AbstractVector{<:Atom})
```

Iterator for the residues (or molecules) of a selection. 

### Example

```jldoctest
julia> using PDBTools

julia> atoms = wget("1LBD");

julia> eachresidue(atoms)
 Residue iterator with length = 238

julia> collect(eachresidue(atoms))
238-element Vector{Residue}[
    SER225A
    ALA226A
    ⋮
    MET461A
    THR462A
]
```
