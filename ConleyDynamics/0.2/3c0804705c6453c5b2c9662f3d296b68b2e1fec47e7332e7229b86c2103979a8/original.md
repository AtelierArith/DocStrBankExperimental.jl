```
convert_spatial_coordinates(coords::Vector{Vector{Float64}},
                            p0::Vector{Float64},
                            p1::Vector{Float64})
```

Convert a given collection of spatial coordinates.

The vector `coords` contains triples of coordinates, which are then transformed to fit into the box with vertices `p0 = (p0x,p0y,p0z)` and `p1 = (p1x,p1y,p1z)`. It is assumed that each coordinate of `p0` is strictly smaller than the corresponding coordinate of `p1`. The function shifts and scales the coordinates in such a way that every side of the box contains at least one point. Upon completion, it returns a new coordinate vector `coordsNew`.

More precisely, if the x-coordinates are spanning the interval `[xmin,xmax]`, the y-coordinates span `[ymin,ymax]`, and the z-coordinates span `[zmin,zmax]`, then the point `(x,y,z)` is transformed to `(xn,yn,zn)` with:

  * `xn = p0x + (p1x-p0x) * (x-cxmin) / (cxmax-cxmin)`
  * `yn = p0y + (p1y-p0y) * (y-cymin) / (cymax-cymin)`
  * `zn = p0z + (p1z-p0z) * (z-czmin) / (czmax-czmin)`
