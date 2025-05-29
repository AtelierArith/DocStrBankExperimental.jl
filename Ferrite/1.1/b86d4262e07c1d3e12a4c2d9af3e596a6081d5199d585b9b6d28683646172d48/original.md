```
SubDofHandler(dh::AbstractDofHandler, cellset::AbstractVecOrSet{Int})
```

Create an `sdh::SubDofHandler` from the parent `dh`, pertaining to the cells in `cellset`. This allows you to add fields to parts of the domain, or using different interpolations or cell types (e.g. `Triangles` and `Quadrilaterals`). All fields and cell types must be the same in one `SubDofHandler`.

After construction any number of discrete fields can be added to the SubDofHandler using [`add!`](@ref). Construction is finalized by calling [`close!`](@ref) on the parent `dh`.

# Examples

We assume we have a `grid` containing "Triangle" and "Quadrilateral" cells, including the cellsets "triangles" and "quadilaterals" for to these cells.

```julia
dh = DofHandler(grid)

sdh_tri = SubDofHandler(dh, getcellset(grid, "triangles"))
ip_tri = Lagrange{RefTriangle, 2}()^2 # vector interpolation for a field u
add!(sdh_tri, :u, ip_tri)

sdh_quad = SubDofHandler(dh, getcellset(grid, "quadilaterals"))
ip_quad = Lagrange{RefQuadrilateral, 2}()^2 # vector interpolation for a field u
add!(sdh_quad, :u, ip_quad)

close!(dh) # Finalize by closing the parent
```
