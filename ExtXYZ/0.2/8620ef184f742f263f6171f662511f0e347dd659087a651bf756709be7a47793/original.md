```
iread_frames(file[, range])
```

Return a Channel for reading from an ExtXYZ file. Frames are yielded one by one. `range` can be a single integer, range object or integer array of frame indices.

Example usage:

```julia
ch = iread_frames("file.xyz")
for frame in ch
    process(frame)
end
```
