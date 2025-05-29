```
readframetrcs(io, idx...)
```

Out-of-place read of a single frame (traces only) from a JavaSeis dataset.  For non full frame, the resulting traces are left justified.  Examples:

# 3D:

```julia
frm_idx = 1
trcs = readframetrcs(jsopen("data_3D.js"), frm_idx)
```

# 4D:

```julia
frm_idx, vol_idx = 1, 1
trcs = readframetrcs(jsopen("data_4D.js"), frm_idx, vol_idx)
```

# 5D:

```julia
frm_idx, vol_idx, hyp_idx = 1, 1, 1
trcs = readframetrcs(jsopen("data_5D.js"), frm_idx, vol_idx, hyp_idx)
```
