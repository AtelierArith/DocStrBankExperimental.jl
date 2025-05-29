```
mdlovofit(
    simulation::Simulation; 
    fraction::AbstractFloat, 
    output_name::Union{String,Nothing} = nothing, 
    reference_frame::Int = 1, 
    maxframes=nothing
)
```

Run MDLovoFit on a trajectory, aligning only the atoms which are in the fraction of the structure with the lowest RMSD. Only CA atoms of protein residues are considered.

Arguments:

  * `simulation` is a Simulation object, with the trajectory of the system and the atom data.
  * `fraction` is the fraction of atoms to be considered in the alignment.

Optional arguments:

  * `output_name=nothing` is the base name of the output files. If nothing, default names will be used.
  * `reference_frame=1` is the index of the frame to be used as reference for the alignment.
  * `maxframes=nothing` is the number of frames to be considered. If nothing, 100 frames are considered.   Set to `length(simulation)` to consider all frames.

Output: 

  * `MDLovoFitResult` data structure with the results of the alignment.

and the output files:

  * `output_name_rmsf.dat` with the RMSF data.
  * `output_name_rmsd.dat` with the RMSD data.
  * `output_name_aligned.pdb` with the aligned structure.

## Example

```jldoctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> md = mdlovofit(sim, fraction=0.7, output_name="mdlovofit_50")
-------------------------------------------------------------------
MDLovoFitResult: Simulation(structure.pdb, trajectory.dcd)

-------------------------------------------------------------------

Aligned pdb file: mdlovofit_50_aligned.pdb
RMSF data file: mdlovofit_50_rmsf.dat
RMSD data file: mdlovofit_50_rmsd.dat

Number of frames considered: 5
Average RMSD of all atoms: 1.79
Average RMSD of the 70.0% atoms of lowest RMSD: 0.53
Average RMSD of the 30.0% atoms of highest RMSD: 4.71

Frame indices availabe in field: frame_indices
RMSD data availabe in fields: rmsd_low, rmsd_high, and rmsd_all

RMSF data availabe in field: rmsf (Number of atoms: 43)
-------------------------------------------------------------------
```
