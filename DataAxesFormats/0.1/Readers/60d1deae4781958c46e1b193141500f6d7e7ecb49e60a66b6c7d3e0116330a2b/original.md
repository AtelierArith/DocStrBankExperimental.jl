```
axis_version_counter(daf::DafReader, axis::AbstractString)::UInt32
```

Return the version number of the axis. This is incremented every time [`delete_axis!`](@ref DataAxesFormats.Writers.delete_axis!) is called. It is used by interfaces to other programming languages to minimize copying data.

!!! note
    This is purely in-memory per-instance, and **not** a global persistent version counter. That is, the version counter starts at zero even if opening a persistent disk `daf` data set.

