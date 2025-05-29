```
getseq(AbstractVector{<:Atom} or filename; selection, code)
```

Returns the sequence of aminoacids from the vector of atoms or file name. Selections may be applied. Code defines if the output will be a one-letter, three-letter or full-residue name array.

### Example

```jldoctest
julia> using PDBTools

julia> protein = read_pdb(PDBTools.TESTPDB);

julia> getseq(protein,"residue < 3")
2-element Vector{String}:
 "A"
 "C"

julia> getseq(protein,"residue < 3", code=2)
2-element Vector{String}:
 "ALA"
 "CYS"

julia> getseq(protein,"residue < 3",code=3)
2-element Vector{String}:
 "Alanine"
 "Cysteine"

```
