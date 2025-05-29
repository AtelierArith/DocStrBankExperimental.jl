```
readhdrs!(io, hdrs, smp_range, trace_range, range...)
```

In-place read of a subset of data (headers only) from a JavaSeis file. If performance is important, then consider using `readframehdrs!` instead.  Examples:

# 3D:

```julia
readhdrs!(jsopen("data_3D.js"), hdrs, :, :, :)
readhdrs!(jsopen("data_3D.js"), hdrs, :, 1:2:end, 1:5)
```

# 4D:

```julia
readhdrs!(jsopen("data_4D.js"), hdrs, :, :, :, :)
readhdrs!(jsopen("data_4D.js"), hdrs, :, :, 2, 2:2:10)
```

# 5D:

```julia
readhdrs!(jsopen("data_5D.js"), hdrs, :, :, :, :, :)
readhdrs!(jsopen("data_5D.js"), hdrs, :, :, 2, 2:2:10, 1:10)
```
