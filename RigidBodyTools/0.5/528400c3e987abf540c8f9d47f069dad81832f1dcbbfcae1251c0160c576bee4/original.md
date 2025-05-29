```
NACA4(n4::Int,ds::Float64,[len=1.0]) <: Body{N}
```

Generates points in the shape of a NACA 4-digit airfoil, specified by `n4`, with distance between points specified by `ds`. The optional parameter `len` specifies the chord length, which defaults to 1.0.

# Example

```jldoctest
julia> b = NACA4(0012,0.02);
```
