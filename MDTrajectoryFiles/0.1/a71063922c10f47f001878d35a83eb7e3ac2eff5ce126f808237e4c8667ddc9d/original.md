```
read_atoms(file::XtcFile, frame::Integer, coords::AbstractMatrix{T}, selection::BitVector) where {T <: Real}
```

Reads atom coordinates for a frame.

# Parameters

  * file: must be already opened for "r"
  * frame: must be in 1:nframes
  * coords: must be preallocated with dimension (3, count(selection))
  * selection: must have length = natoms
