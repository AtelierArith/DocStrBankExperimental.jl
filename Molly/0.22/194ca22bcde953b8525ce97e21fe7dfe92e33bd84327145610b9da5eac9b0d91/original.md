```
TrajectoryWriter(n_steps, filepath; format="", atom_inds=[],
                 write_velocities=false)
```

Write 3D structures to a file throughout a simulation.

Uses Chemfiles.jl to write to one of a variety of formats including DCD, XTC, CIF, MOL2, SDF, TRR and XYZ. The full list of file formats can be found in the [Chemfiles docs](https://chemfiles.org/chemfiles/latest/formats.html#list-of-supported-formats). By default the format is guessed from the file extension but it can also be given as a string, e.g. `format="DCD"`.

The atom indices to be written can be given as a list or range to `atom_inds`, with all atoms being written by default. Velocities can be written in addition to coordinates by setting `write_velocities=true`. Chemfiles does not support writing velocities to all file formats.

The [`System`](@ref) should have `atoms_data` defined, and `topology` if bonding information is required. The file will be appended to, so should be deleted before simulation if it already exists.

Not compatible with 2D systems.
