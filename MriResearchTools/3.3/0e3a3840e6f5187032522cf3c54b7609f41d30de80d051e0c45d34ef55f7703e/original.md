```
write_emptynii(size, path; datatype=Float32, header=NIVolume(zeros(datatype, 1)).header)
```

Writes an empty NIfTI image to disk that can be used for memory-mapped access.

# Examples

```julia-repl
julia> vol = write_emptynii((64,64,64), "empty.nii")
julia> vol.raw[:,:,1] .= ones(64,64) # synchronizes mmapped file on disk
```

Warning: MRIcro can only open images with types Int32, Int64, Float32, Float64
