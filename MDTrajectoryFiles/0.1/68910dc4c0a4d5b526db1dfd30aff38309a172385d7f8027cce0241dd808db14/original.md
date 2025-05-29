```
write_frame(file::XtcFile, step::Integer, time::Real, box::AbstractMatrix{S}, 
                coords::AbstractMatrix{T}) where {S, T <: Real}
```

# Parameters

```
- file: must be already opened for "w" or "a"
- step: integration step 
- time: frame time (ps)
- box: dimension (3, 3)
- coords: dimension (3, natoms)
```
