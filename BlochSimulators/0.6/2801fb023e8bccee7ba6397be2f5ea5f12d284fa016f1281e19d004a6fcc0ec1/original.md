```
gpu(x)
```

Move `x` to CUDA device. It uses `Functors.fmap` to recursively traverse the fields of the struct `x`, converting `<:AbstractArrays` to `CuArrays`, and ignoring isbitsarrays. For custom structs (e.g. `<:BlochSimulator` or `<:AbstractTrajectory`), it is required that `typeof(x)` be made a `Functors.@functor` (e.g. `@functor FISP`).
