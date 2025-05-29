```julia
read_step(
    trajectory::Chemfiles.Trajectory,
    step::Integer
) -> Chemfiles.Frame

```

指定された`step`の`trajectory`を読み取り、対応する`Frame`を返します。
