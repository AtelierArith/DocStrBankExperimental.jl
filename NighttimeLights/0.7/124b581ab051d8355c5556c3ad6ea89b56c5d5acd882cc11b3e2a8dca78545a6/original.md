Applies a function to each timeseries of a datacube present in a mask. 

# Example:

```
julia> datacube = rand(1:10.0, 10,10,10)
julia> mask = rand(0:1, 10, 10)
julia> iterator(x::Vector) = x .+ 1
julia> long_apply(x, datacube)
```
