```
positions(frame::Chemfiles.Frame)
```

Return the positions of the atoms in a `Chemfiles.Frame` as a `FramePositions` object.

This is the default way to access the positions of the atoms in a simulation.

# Example

```julia-repl # to be doctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> frame = current_frame(simulation);

julia> p = positions(frame);

julia> p[1].x 
5.912472724914551

```
