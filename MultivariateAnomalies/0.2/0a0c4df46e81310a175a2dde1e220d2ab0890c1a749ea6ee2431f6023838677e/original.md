```
mw_AVG(datacube::AbstractArray{tp,N}, windowsize::Int = 10) where {tp,N}
```

compute the average in a moving window along the first dimension of the datacube (presetting: `windowsize = 10`). Accepts N dimensional datacubes.

# Examples

```
julia> dc = randn(50,3,3,3)
julia> mw_AVG(dc, 15)
```
