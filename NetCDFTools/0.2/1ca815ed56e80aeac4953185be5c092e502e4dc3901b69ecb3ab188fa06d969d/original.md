```
MFDataset(fs) = MFDataset(; fs)
MFDataset(fs, chunksize) = MFDataset(; fs, chunksize)
```

# Examples

```julia
m = MFDataset(fs)
v = m["LAI"]
data = v[i, j]
```
