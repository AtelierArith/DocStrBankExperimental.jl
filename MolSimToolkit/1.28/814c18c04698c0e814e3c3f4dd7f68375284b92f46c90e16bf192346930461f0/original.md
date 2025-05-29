```
first_frame!(simulation::Simulation)
```

Restarts the trajectory buffer, and places the current frame at the first frame in the trajectory.

# Example

```julia-repl
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj; first=3);

julia> first_frame!(simulation) 
Simulation 
    Atom type: Atom{Nothing}
    PDB file: /test/data/namd/protein_in_popc_membrane/structure.pdb
    Trajectory file: /test/data/namd/protein_in_popc_membrane/trajectory.dcd
    Total number of frames: 5
    Frames to consider: 1, 2, 3, 4, 5
    Number of frames to consider: 5
    Current frame: 3

```
