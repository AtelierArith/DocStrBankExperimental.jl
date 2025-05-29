```
mw_COR(datacube::Array{tp, 4}, windowsize::Int = 10) where {tp}
```

compute the correlation in a moving window along the first dimension of the datacube (presetting: `windowsize = 10`). Accepts 4-dimensional datacubes.
