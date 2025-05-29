```
read_atoms(file::XtcFile, frame::Integer, coords::AbstractMatrix{T}) where {T <: Real}
```

Reads atom coordinates for a frame.

# Parameters

  * file: must be already opened for "r"
  * frame: must be in 1:nframes
  * coords: must be preallocated with dimension (3, natoms)
