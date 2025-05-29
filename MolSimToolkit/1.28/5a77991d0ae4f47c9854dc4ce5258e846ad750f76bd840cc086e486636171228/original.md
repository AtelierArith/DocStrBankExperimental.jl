```
map_fractions(simulation::Simulation; maxframes=nothing)
```

Run MDLovoFit on a trajectory, to obtain the RMSD of the fractions of the structure with the lowest RMSD, the fraction with the highest RMSD, and the whole structure.

Only CA atoms of protein residues are considered. 

Argument:

  * `simulation` is a Simulation object, with the trajectory of the system and the atom data.

Keyword arguments:

  * `maxframes=nothing` is the number of frames to be considered. If nothing, 100 frames are considered.   Set to `length(simulation)` to consider all frames.

## Example

```jldoctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> mf = map_fractions(sim)
-------------------------------------------------------------------
MapFractionsResult: Simulation(structure.pdb, trajectory.dcd)

-------------------------------------------------------------------
Fields: 
- fraction: fraction of atoms considered in the alignment.
- frame_indices: the frame index of each frame considered.
- rmsd_low: RMSD of the fraction of the structure with the lowest RMSD.
- rmsd_high: RMSD of the fraction not considered for the alignment.
- rmsd_all: RMSD of the whole structure.

Greatest fraction for which the RMSD-low is smaller than 1.0: 0.79
                                                         2.0: 0.9
                                                         3.0: 0.99
-------------------------------------------------------------------
```
