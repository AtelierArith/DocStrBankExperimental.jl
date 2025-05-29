```
mw_VAR!(out::Array{tp, N}, datacube0mean::Array{tp,N}, windowsize::Int = 10) where {tp,N}
```

mutating version for `mw_VAR()`. The mean of the input data `datacube0mean` has to be 0. Initialize out properly: `out = datacube0mean` leads to wrong results.
