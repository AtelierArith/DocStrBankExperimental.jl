```
naca4(cam,pos,t[;np=20][,Zc=0.0+0.0im][,len=1.0]) -> Vector{Complex128}
```

Generates the vertices of a NACA 4-digit airfoil of chord length 1. The relative camber is specified by `cam`, the position of maximum camber (as fraction of chord) by `pos`, and the relative thickness by `t`.

The optional parameter `np` specifies the number of points on the upper or lower surface. The optional parameter `Zc` specifies the mean position of the vertices (which is set to the origin by default). The optional parameter `len` specifies the chord length.

# Example

```jldoctest
julia> w = naca4(0.0,0.0,0.12);

julia> p = Polygon(w);
```
