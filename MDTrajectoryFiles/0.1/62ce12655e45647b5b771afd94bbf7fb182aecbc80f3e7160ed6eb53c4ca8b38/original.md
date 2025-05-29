```
read_box(file::DcdFile, frame::Integer, box::AbstractVector{T}) where {T <: Real}
```

# Parameters

```
- file: must be already opened for "r"
- frame: must be in 1:nframes
- box: must be preallocated with dimension (6,)
```
