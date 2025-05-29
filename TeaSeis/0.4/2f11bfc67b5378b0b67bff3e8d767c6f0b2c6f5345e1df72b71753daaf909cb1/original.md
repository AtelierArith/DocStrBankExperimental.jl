```
readtrcs(io, sample_range, trace_range, range...)
```

Out-of-place read of a subset of data (traces only) from a JavaSeis file. Returns an array of trace data. If performance is important, then consider using `readframetrcs` instead.  Examples:

# 3D:

```julia
trcs = readtrcs(jsopen("data_3D.js"), :, :, :)
trcs = readtrcs(jsopen("data_3D.js"), :, 1:2:end, 1:5)
```

# 4D:

```julia
trcs = readtrcs(jsopen("data_4D.js"), :, :, :, :)
trcs = readtrcs(jsopen("data_4D.js"), :, :, 2, 2:2:10)
```

# 5D:

```julia
trcs = readtrcs(jsopen("data_5D.js"), :, :, :, :, :)
trcs = readtrcs(jsopen("data_5D.js"), :, :, 2, 2:2:10, 1:10)
```
