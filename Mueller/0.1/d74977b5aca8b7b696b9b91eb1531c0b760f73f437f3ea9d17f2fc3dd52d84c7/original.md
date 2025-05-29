```
linear_polarizer([T=Float64], θ=0; p=1)
```

A linear polarizer with the throughput axis given by `θ`, in radians, by default horizontal. The partial polarization can be given with the `p` keyword argument, which changes the intensity by a factor of `p^2/2`.

# Examples

```jldoctest
julia> M = linear_polarizer()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 0.5  0.5  0.0  0.0
 0.5  0.5  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> S = [1, 0, 0, 0]; # I, Q, U, V

julia> M * S # only horizontal component (+Q) remains
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 0.5
 0.5
 0.0
 0.0
```
