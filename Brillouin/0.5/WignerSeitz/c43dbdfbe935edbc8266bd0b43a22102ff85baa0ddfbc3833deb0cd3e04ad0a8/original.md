```
wignerseitz(basis::AbstractVector{<:SVector{D}}; merge::Bool = true, Nmax = 3)
wignerseitz(basis::AbstractVector{<:AbstractVector}; merge::Bool = true, Nmax = 3)
                                                            --> Cell{D}
```

Given a provided basis, return a `Cell{D}` containing the vertices and associated (outward oriented) faces of the Wigner-Seitz cell defined by `basis` in `D` dimensions. The returned vertices are given in the the basis of `basis` (see [`cartesianize!`](@ref) for conversion).

## Keyword arguments

  * `merge` (default, `true`): if `true`, co-planar faces are merged to form polygonal planar faces (e.g., triangles, quadrilaterals, and ngons generally). If `false`, raw "unprocessed" triangles (`D=3`) and segments (`D=2`) are returned instead. `merge` has no impact for `D=1`.
  * `Nmax` (default, `3`): includes `-Nmax:Nmax` points in the initial lattice used to generate the underlying Voronoi tesselation. It is unwise to set this to anything lower than 3 without explicitly testing convergence; and probably unnecessary to increase it beyond 3 as well.
