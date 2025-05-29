```
boundarymap(p, bd, t [,intervals]) → bmap, arclengths
```

Compute the boundary map of the particle `p` in the billiard `bd` by evolving the particle for total amount `t` (either float for time or integer for collision number).

Return a vector of 2-vectors `bmap` and also `arclengths(bd)`. The first entry of each element of `bmap` is the arc-coordinate at collisions $\xi$, while the second  is the sine of incidence angle $\sin(\phi_n)$.

The measurement direction of the arclengths of the individual obstacles is dictated by their order in `bd`. The sine of the angle is computed *after* specular reflection has taken place.

The returned values of this function can be used in conjuction with the function [`bdplot_boundarymap`](@ref) (requires `using PyPlot`) to plot the boundary map in an intuitive way.

*Notice* - this function only works for normal specular reflection. Random reflections or ray-splitting will give unexpected results.

See also [`to_bcoords`](@ref), [`boundarymap_portion`](@ref). See [`parallelize`](@ref) for a parallelized version.
