```
write_frame(file::DcdFile, box::AbstractVector{S}, 
                coords::AbstractMatrix{T}) where {S, T <: Real}
```

# Parameters

```
- file: must be already opened for "w" or "a"
- box dimension (6, ) The interpretation of these
  parameter varies with the program and version
- coords: must be preallocated with dimension (3, natoms)
```
