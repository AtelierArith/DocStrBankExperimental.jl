```
residue_residue_distance(
    r1::PDBTools.Residue, 
    r2::PDBTools.Residue; 
    positions::AbstractVector{AbstractVector{T}}=nothing; 
    unitcell=nothing
)
```

Calculate the minimum distance between two residues in a protein structure.  If the `positions` argument is not provided, the function calculates the distance using the coordinates of the atoms in the residues. If `positions` is provided, the function uses the coordinates in the positions array. 

# Arguments

  * `r1::PDBTools.Residue`: Residue 1
  * `r2::PDBTools.Residue`: Residue 2
  * `positions::AbstractVector{AbstractVector{T}}`: Optional alternate positions of the atoms in the structure.
  * `unitcell=nothing`: Optional unit cell dimensions for periodic boundary conditions.

!!! note
    The index of the atoms in the residues must match the index of the atoms in the positions array.


# Example

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> residues = collect(eachresidue(ats));

julia> r1 = residues[1]; r10 = residues[10];

julia> println(name(r1), resnum(r1), " and ", name(r10), resnum(r10))
LYS211 and GLU220

julia> d = residue_residue_distance(r1, r10)
16.16511f0
```
