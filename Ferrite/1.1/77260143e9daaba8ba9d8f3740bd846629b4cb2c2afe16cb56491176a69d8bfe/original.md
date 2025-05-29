```
DofHandler(grid::Grid)
```

Construct a `DofHandler` based on the grid `grid`.

After construction any number of discrete fields can be added to the DofHandler using [`add!`](@ref). Construction is finalized by calling [`close!`](@ref).

By default fields are added to all elements of the grid. Refer to [`SubDofHandler`](@ref) for restricting fields to subdomains of the grid.

# Examples

```julia
dh = DofHandler(grid)
ip_u = Lagrange{RefTriangle, 2}()^2 # vector interpolation for a field u
ip_p = Lagrange{RefTriangle, 1}()   # scalar interpolation for a field p
add!(dh, :u, ip_u)
add!(dh, :p, ip_p)
close!(dh)
```

!!! note "Numbering of degree of freedom"
    Note that the numbering of degrees of freedom do *NOT* follow the global numbering of nodes in the associated grid.

