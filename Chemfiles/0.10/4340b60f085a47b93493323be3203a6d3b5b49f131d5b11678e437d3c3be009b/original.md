```julia
set_cell!(
    trajectory::Chemfiles.Trajectory,
    cell::Chemfiles.UnitCell
)

```

Set the `cell` associated with a `trajectory`. This cell will be used when reading and writing the file, replacing any unit cell in the file.
