```
coordination_number(
    sim::Simulation,
    solute::AbstractVector{<:PDBTools.Atom},
    solvent::AbstractVector{<:PDBTools.Atom};
    solvent_natomspermol::Integer,
    cutoff::Real,
    show_progress::Bool = true
)
```

Calculate the coordination number of the solute atoms with the solvent atoms.

!!! note
    The distance considered is the **minimum distance** between the solute atoms  and the atoms of each solvent molecule.


# Positional Arguments

  * `sim::Simulation`: Simulation object.
  * `solute::AbstractVector{<:PDBTools.Atom}`: Vector of solute atoms.
  * `solvent::AbstractVector{<:PDBTools.Atom}`: Vector of solvent atoms.

# Keyword Arguments

  * `solvent_natomspermol::Integer`: Number of atoms per solvent molecule.
  * `cutoff::Real`: Cutoff distance.
  * `show_progress::Bool`: Show progress bar. (optional, default: `true`)

# Returns

  * `cn::Vector{Int}`: Vector with the coordination number of the solute atoms with the solvent atoms, at each frame.

# Example

```jldoctest
julia> using MolSimToolkit, PDBTools, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd2_pdb, Testing.namd2_traj; frames=1:5);

julia> protein = select(atoms(sim), "protein");

julia> tmao = select(atoms(sim), "resname TMAO");

julia> coordination_number(sim, protein, tmao; solvent_natomspermol=14, cutoff=3.0, show_progress=false)
5-element Vector{Int64}:
 7
 3
 4
 5
 6

```
