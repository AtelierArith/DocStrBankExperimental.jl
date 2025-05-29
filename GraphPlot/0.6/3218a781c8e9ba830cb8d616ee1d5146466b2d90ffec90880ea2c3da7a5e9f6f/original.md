This function is copy from [IainNZ](https://github.com/IainNZ)'s [GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl)

Use a modified version of the spring/repulsion model of Fruchterman and Reingold (1991):

  * Attractive force:  f_a(d) =  d / k
  * Repulsive force:  f_r(d) = -k^2 / d^2

where d is distance between two vertices and the optimal distance between vertices k is defined as C * sqrt( area / num_vertices ) where C is a parameter we can adjust

**Parameters**

*g* a graph

*C* Constant to fiddle with density of resulting layout

*MAXITER* Number of iterations we apply the forces

*INITTEMP* Initial "temperature", controls movement per iteration

*seed* Integer seed for pseudorandom generation of locations (default = 0).

**Examples**

```
julia> g = smallgraph(:karate)
julia> locs_x, locs_y = spring_layout(g)
```
