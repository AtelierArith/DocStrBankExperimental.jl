```
copyto!(output_buffer::AbstractArray{T}, obj::Union{DatasetOrAttribute}) where T
```

Copy [part of] a HDF5 dataset or attribute to a preallocated output buffer. The output buffer must be convertible to a pointer and have a contiguous layout.
