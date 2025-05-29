```
euclidean_graph(points)
```

Given the `d×N` matrix `points` build an Euclidean graph of `N` vertices and return a graph and Dict containing the distance on each edge.

### Optional Arguments

  * `L=1`: used to bound the `d` dimensional box from which points are selected.
  * `p=2`
  * `bc=:open`

### Implementation Notes

Defining the `d`-dimensional vectors `x[i] = points[:,i]`, an edge between vertices `i` and `j` is inserted if `norm(x[i]-x[j], p) < cutoff`. In case of negative `cutoff` instead every edge is inserted. For `p=2` we have the standard Euclidean distance. Set `bc=:periodic` to impose periodic boundary conditions in the box $[0,L]^d$.

## Examples

```jldoctest
julia> pts = rand(3, 10); # 10 vertices in R^3

julia> g, dists = euclidean_graph(pts, p=1, bc=:periodic) # Taxicab-distance (L^1);

julia> g
{10, 45} undirected simple Int64 graph
```
