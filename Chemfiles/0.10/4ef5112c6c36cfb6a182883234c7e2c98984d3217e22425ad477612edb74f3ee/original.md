```julia
Trajectory(path::AbstractString) -> Chemfiles.Trajectory
Trajectory(
    path::AbstractString,
    mode::Char
) -> Chemfiles.Trajectory
Trajectory(
    path::AbstractString,
    mode::Char,
    format::AbstractString
) -> Chemfiles.Trajectory

```

Opens the trajectory file at the given `path`.

The opening `mode` can be `'r'` for read, `'w'` for write or `'a'` for append, and defaults to `'r'`. The optional `format` parameter give a specific file format to use when opening the file.
