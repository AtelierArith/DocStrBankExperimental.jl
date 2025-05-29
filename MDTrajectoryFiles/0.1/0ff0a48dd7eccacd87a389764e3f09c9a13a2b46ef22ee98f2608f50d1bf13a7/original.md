```
read_box(file::XtcFile, frame::Integer, box::AbstractMatrix{T}) where {T <: Real}
```

# Parameters

```
- file: must be already opened for "r"
- frame: must be in 1:nframes
- box: must be preallocated with dimension (3, 3)
```
