```julia
read_step(
    trajectory::Chemfiles.Trajectory,
    step::Integer
) -> Chemfiles.Frame

```

Read the given `step` of the `trajectory`, and return the corresponding `Frame`.
