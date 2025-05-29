```
NACA4(cam,pos,thick,ds::Float64,[len=1.0]) <: Body{N}
```

Generates points in the shape of a NACA 4-digit airfoil. The relative camber is specified by `cam`, the position of maximum camber (as fraction of chord) by `pos`, and the relative thickness by `thick`. The parameter `ds` specifies the distance between points. The optional parameter `len` specifies the chord length, which defaults to 1.0.

# Example

```jldoctest
julia> b = NACA4(0.0,0.0,0.12,0.02);
```
