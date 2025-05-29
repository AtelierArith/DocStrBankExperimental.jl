```
randn_pvector2d(n::Integer, T::DataType = Float64)
randn_pvector2d(n::Integer, u::Units, T::DataType = Float64)
randn_pvector(n::Integer, T::DataType = Float64)
randn_pvector(n::Integer, u::Units, T::DataType = Float64)
```

Generate uniformly distributed PVectors

## Examples

```julia
julia> p = randn_pvector(5)
julia> pu = randn_pvector2d(5, u"m")
```
