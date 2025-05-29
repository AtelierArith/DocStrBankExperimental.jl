```
bulk_coordination(
    simulation::Simulation;
    reference_solute::AbstractVector{<:PDBTools.Atom}, 
    solute::AbstractVector{<:PDBTools.Atom},
    n_atoms_per_molecule_solute::Integer,
    solvent::AbstractVector{<:PDBTools.Atom}, 
    n_atoms_per_molecule_solvent::Integer,
    dmax::Real = 5.0,
    cutoff::Real = 20.0,
    bin_size::Real = 0.1,
    show_progress = true,
)
```

Computes the coordination number of one type of solvent molecule relative to another  solvent molecule, as a function of the distance to a reference solute molecule. 

For example, imagine a protein solvated in a mixture of water and TMAO. This function allows to compute the number of water molecules that are within a given distance to the TMAO molecules, as a function of the distance to the protein. That is, it computes the coordination number of water relative to TMAO, as a function of the distance to the protein.

The function returns the the distances and the histogram of the coordination number as a function of  the distance.

!!! compat
    This function was introduced in version 1.11.0 of MolSimToolkit.jl.


# Arguments

  * `simulation::Simulation`: The simulation object
  * `reference_solute::AbstractVector{PDBTools.Atom}`: The atoms of the reference solute molecule  (the protein in the example above).
  * `solute::AbstractVector{PDBTools.Atom}`: The atoms of the solute molecule (the TMAO in the example above).
  * `n_atoms_per_molecule_solute::Integer`: The number of atoms per molecule of the solute.
  * `solvent::AbstractVector{PDBTools.Atom}`: The atoms of the solvent molecule (the water in the example above).
  * `n_atoms_per_molecule_solvent::Integer`: The number of atoms per molecule of the solvent.
  * `dmax::Real = 5.0`: The maximum distance to the solute to consider a solvent molecule as coordinated.
  * `cutoff::Real = 20.0`: The maximum distance to the reference molecule for computing the histogram.
  * `bin_size::Real = 0.1`: The size of the bins for the histogram.
  * `show_progress = true`: Whether to show a progress bar.

# Example

```julia-repl
julia> using MolSimToolkit, PDBTools

julia> pdb = readPDB(MolSimToolkit.Testing.namd2_pdb); # protein-tmao-water system

julia> trajectory = MolSimToolkit.Testing.namd2_traj;

julia> simulation = Simulation(pdb, trajectory)
Simulation 
    Atom type: Atom
    PDB file: -
    Trajectory file: /home/leandro/.julia/dev/MolSimToolkit/test/data/namd/protein_in_water_tmao/trajectory.dcd
    Total number of frames: 20
    Frame range: 1:1:20
    Number of frames in range: 20
    Current frame: nothing

julia> r, h = bulk_coordination(
           simulation;
           reference_solute = select(pdb, "protein"),
           solute = select(pdb, "resname TMAO"),
           n_atoms_per_molecule_solute = 14,
           solvent = select(pdb, "water"),
           n_atoms_per_molecule_solvent = 3,
       );

julia> using Plots

julia> plot(r, h, # plots `h` as a function of `r`
           xlabel = "Distance to protein (Å)",
           ylabel = "TMAO-water Coordination number",
           linewidth=2,
           label=:none, framestyle=:box, fontfamily="Computer Modern",
       )
```
