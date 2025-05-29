```
residue_ticks(
    atoms (or) residues (or) residue iterator; 
    first=nothing, last=nothing, stride=1, oneletter=true, serial=false
)
```

Returns a tuple with residue numbers and residue names for the given atoms, to be used as tick labels in plots.

The structure data can be provided a vector of `Atom`s, a vector of `Residue`s or an `eachresidue` iterator. 

`first` and `last` optional keyword parameters are integers that refer to the residue numbers to be included.  The `stride` option can be used to skip residues and declutter the tick labels.

If `oneletter` is `false`, three-letter residue codes are returned. Residues with unknown names will be  named `X` or `XXX`. 

If `serial=true` the sequential residue index will be used as the index of the ticks. If instead `serial=false`, the positions will be set to the residue numbers.

# Examples

```jldoctest
julia> using PDBTools

julia> atoms = wget("1LBD", "protein");

julia> residue_ticks(atoms; stride=50) # Vector{<:Atom} as input
(Int32[225, 275, 325, 375, 425], ["S225", "Q275", "L325", "L375", "L425"])

julia> residue_ticks(atoms; first=235, last=240) # first=10
(Int32[235, 236, 237, 238, 239, 240], ["I235", "L236", "E237", "A238", "E239", "L240"])

julia> residue_ticks(eachresidue(atoms); stride=50) # residue iterator as input
(Int32[225, 275, 325, 375, 425], ["S225", "Q275", "L325", "L375", "L425"])

julia> residue_ticks(collect(eachresidue(atoms)); stride=50) # Vector{Residue} as input
(Int32[225, 275, 325, 375, 425], ["S225", "Q275", "L325", "L375", "L425"])

julia> residue_ticks(atoms; first=10, stride=50, serial=true) # using serial=true
(10:50:210, ["R234", "K284", "R334", "S384", "E434"])

```

The resulting tuple of residue numbers and labels can be used as `xticks` in `Plots.plot`, for example.
