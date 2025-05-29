```julia
velocities(
    frame::Chemfiles.Frame
) -> Chemfiles.ChemfilesArray

```

Get the velocities in a `Frame` as an array. The velocities are readable and writable from this array. If the frame is resized (by writing to it, or calling `resize!`), the array is invalidated.

If the frame do not have velocity, this function will error. You can use `add_velocities!` to add velocities to a frame before calling this function.
