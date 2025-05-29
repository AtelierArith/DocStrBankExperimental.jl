```
writeframe(io, trcs, idx...)
```

Write a frame of data to the JavaSeis dataset corresponding to `io::JSeis`.  `trcs` is a 2-dimensional array.  The location of the datset written to is determined by `idx...`.  For example:

# 3D:

```julia
writeframe(jsopen("data_3D.js"), trcs, 1) # write to frame 1
```

# 4D:

```julia
writeframe(jsopen("data_4D.js"), trcs, 1, 2) # write to frame 1, volume 2
```

# 5D:

```julia
writeframe(jsopen("data_5D.js"), trcs, 1, 2, 3) # write to frame 1, volume 2, hypercube 3
```
