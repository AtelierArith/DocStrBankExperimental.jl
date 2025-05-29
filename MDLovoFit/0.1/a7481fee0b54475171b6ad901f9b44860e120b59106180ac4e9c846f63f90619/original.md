```
mdlovofit(
    atoms::AbstractVector{<:PDBTools.Atom}, # atoms of the system (usually a "protein and name CA" selection)
    trajectory_file::String, # name of the trajectory file 
    fraction; # fraction of atoms to be aligned
    output_pdb=nothing, # name of the output file. If nothing, no output file is written
    atoms_to_consider=atoms, # may be a different set of atoms
    first=1, 
    last=nothing, # nothing means the last frame of the trajectory
    iref=1, # reference frame
    maxframes=100, # number of frames to be aligned
)
```

Run MDLovoFit on a trajectory.
