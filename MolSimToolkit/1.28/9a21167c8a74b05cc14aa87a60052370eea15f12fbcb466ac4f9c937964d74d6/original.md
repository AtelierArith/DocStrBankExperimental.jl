```
average_dihedrals(sim::Simulation, v::AbstractVector{<:AbstractVector{<:Integer}}; degrees=true)
average_dihedrals(sim::Simulation, v::AbstractVector{<:AbstractVector{<:PDBTools.Atom}}; degrees=true)
```

Computes the average dihedral angles for many sets of 4 vectors from a trajectory. The input is a vector of vectors,  containing the indices of the atoms forming the dihedral angles, or the `PDBTools.Atom` objects. 

The function returns a vector with the average dihedral angles in radians or degrees.

## Example

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing, PDBTools

julia> atoms = read_pdb(Testing.namd2_pdb);

julia> cAs = select(atoms, "name CA and residue < 5"); # 4 atoms

julia> r1b = select(atoms, "residue 1 and backbone"); # 4 atoms

julia> inds = [ index.(cAs), index.(r1b) ]; # List of vector of indices

julia> sim = Simulation(Testing.namd2_pdb, Testing.namd2_traj);

julia> ds = average_dihedrals(sim, inds)
2-element Vector{Float64}:
 -60.12860673875001
  -0.3398274578758668

julia> ats = [ cAs, r1b ]; # List of vectors of PDBTools.Atom

julia> ds = average_dihedrals(sim, ats)
2-element Vector{Float64}:
 -60.12860673875001
  -0.3398274578758668

```
