```
MFDataset(fs) = MFDataset(; fs)
MFDataset(fs, chunksize) = MFDataset(; fs, chunksize)
```

# 例

```julia
m = MFDataset(fs)
v = m["LAI"]
data = v[i, j]
```
