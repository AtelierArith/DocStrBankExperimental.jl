```julia
positions(
    frame::Chemfiles.Frame
) -> Chemfiles.ChemfilesArray

```

Get the positions in a `Frame` as an array. The positions are readable and writable from this array. If the frame is resized (by writing to it, or calling `resize!`), the array is invalidated.
