```
readtrcs!(io, trcs, sample_range, trace_range, range...)
```

In-place read of a subset of data (traces only) from a JavaSeis file. If performance is important, then consider using `readframetrcs!` instead.  Examples:

# 3D:

```julia
readtrcs!(jsopen("data_3D.js"), trcs, :, :, :)
readtrcs!(jsopen("data_3D.js"), trcs, :, 1:2:end, 1:5)
```

# 4D:

```julia
readtrcs!(jsopen("data_4D.js"), trcs, :, :, :, :)
readtrcs!(jsopen("data_4D.js"), trcs, :, :, 2, 2:2:10)
```

# 5D:

```julia
readtrcs!(jsopen("data_5D.js"), trcs, :, :, :, :, :)
readtrcs!(jsopen("data_5D.js"), trcs, :, :, 2, 2:2:10, 1:10)
```
