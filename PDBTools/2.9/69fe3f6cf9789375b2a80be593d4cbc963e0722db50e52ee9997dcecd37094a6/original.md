```
contact_map(
    atoms1::AbstractVector{<:PDBTools.Atom}
    atoms2::AbstractVector{<:PDBTools.Atom}; # optional for contacts between two structures
    dmax::Real=4.0,
    gap::Int=0, # only available if atoms2 is not provided
    unitcell=nothing,
    discrete::Bool=true,
    positions::Union{Nothing,AbstractVector{<:AbstractVector{<:Real}}}=nothing,
)
```

Calculate the contact map between residues in a protein* structure (if only  `atoms1` is provided) or between residues in two different protein* structures (`atoms1` and `atoms2`). 

!!! note
    The distance used to define a contact is the **minimum** distance between any two atoms of the residues of the atoms groups provided, with a  threshold distance `dmax`.


Returns the contact map as a `ContactMap` object.

*The term "protein" is used here to refer to any structure with residues.

# Arguments

  * `atoms1::AbstractVector{<:PDBTools.Atom}`: Atoms of the first structure.
  * `atoms2::AbstractVector{<:PDBTools.Atom}`: Atoms of the second structure, if provided.

# Optional keyword arguments

  * `dmax::Real=4.0`: Threshold distance for a contact.
  * `gap::Int=0`: Gap between residues to calculate contacts.
  * `unitcell=nothing`: Unit cell dimensions for periodic boundary conditions.
  * `discrete::Bool=true`: If `true`, the matrix contains `Bool` values, where `true`  indicates a contact and `false` indicates no contact.  If `false`, the matrix contains distances between residues.
  * `positions`: Positions of the atoms in the structure. If provided, the function uses these  positions to calculate the distance between residues.

# Examples

## Contact map between residues in the same structure

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> cA = select(ats, "chain A");

julia> cB = select(ats, "chain B");

julia> map = contact_map(cA, cB) # contact map between chains A and B
ContactMap{Union{Missing, Bool}} of size (243, 12), with threshold 4.0 and gap 0 

julia> # using Plots; heatmap(map); # uncoment to plot the contact map
```

## Contact map between residues in two different structures

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> cA = select(ats, "chain A");

julia> cB = select(ats, "chain B");

julia> map = contact_map(cA, cB) # contact map between chains A and B
ContactMap{Union{Missing, Bool}} of size (243, 12), with threshold 4.0 and gap 0 

julia> # using Plots; heatmap(map); # uncoment plot the contact map
```
