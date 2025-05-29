```
euclidean_graph(points::Matrix, G; L=1., p=2., cutoff=Inf, bc=:periodic)
```

Given the `d×N` matrix `points` builds an Euclidean graph of `N` vertices according to the following procedure.

Defining the `d`-dimensional vectors `x[i] = points[:,i]`, an edge between vertices `i` and `j` is inserted if `norm(x[i]-x[j], p) < cutoff`. In case of negative `cutoff` instead every edge is inserted. For `p=2` we have the standard Euclidean distance. Set `bc=:periodic` to impose periodic boundary conditions in the box $[0,L]^d$. Set `bc=:open` for open boundary condition. In this case the keyword argument `L` will be ignored.

Returns a graph and Dict containing the distance on each edge.
