```
make_directed_edge_values(lrs::LatticeReactionSystem, x_vals::Tuple{T,T}, y_vals::Tuple{T,T} = (undef,undef),
                 z_vals::Tuple{T,T} = (undef,undef)) where {T}
```

Generates edge parameter values for a lattice reaction system. Only work for (Cartesian or masked) grid lattices (without diagonal adjacencies). Each dimension (x, and possibly y and z), and direction has assigned its own constant edge parameter value.

Input:     - `lrs`: The lattice reaction system for which values should be generated.     - `x_vals::Tuple{T,T}`: The values in the increasing (from a lower x index to a higher x index)     and decreasing (from a higher x index to a lower x index) direction along the x dimension.     - `y_vals::Tuple{T,T}`: The values in the increasing and decreasing direction along the y dimension.     Should only be used for 2 and 3-dimensional grids.     - `z_vals::Tuple{T,T}`: The values in the increasing and decreasing direction along the z dimension.     Should only be used for 3-dimensional grids.

Output:     - `ep_vals`: A sparse matrix of size (num*verts,num*verts) (where num*verts is the number of     vertices in `lrs`). Here, `eps[i,j]` is filled only if there is an edge going from vertex i to     vertex j. The value of `eps[i,j]` is determined by the `x*vals`,`y*vals`, and`z*vals` Tuples,     and vertices i and j's relative position in the grid.

It should be noted that two adjacent vertices will always be different in exactly a single dimension (x, y, or z). The corresponding tuple determines which value is assigned.

Example:     In the following example, we wish to have diffusion in the x dimension, but a constant flow from     low y values to high y values (so not transportation from high to low y). We achieve it in the     following manner:

```julia
using Catalyst
rn = @reaction_network begin
    (p,d), 0 <--> X
end
tr = @transport_reaction D X
lattice = CartesianGrid((5,5))
lrs = LatticeReactionSystem(rn, [tr], lattice)

D_vals = make_directed_edge_values(lrs, (0.1, 0.1), (0.1, 0.0))
```

Here, since we have a 2d grid, we only provide the first two Tuples to `make_directed_edge_values`.
