```julia
read_step!(
    trajectory::Chemfiles.Trajectory,
    step::Integer,
    frame::Chemfiles.Frame
)

```

Read the given `step` of the `trajectory` into an preexisting `Frame` structure.
