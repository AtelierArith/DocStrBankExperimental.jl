```julia
read_step!(
    trajectory::Chemfiles.Trajectory,
    step::Integer,
    frame::Chemfiles.Frame
)

```

与えられた `step` を既存の `Frame` 構造体に読み込みます。
