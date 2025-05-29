```
map_qubo_square(coupling::AbstractVector, onsite::AbstractVector) -> SquareQUBOResult
```

Map a QUBO problem on square lattice to a weighted MIS problem on a grid graph, where the QUBO problem can be specified by

  * a vector coupling of `(i, j, i', j', J)`, s.t. (i', j') == (i, j+1) or (i', j') = (i+1, j).
  * a vector of onsite term `(i, j, h)`.

$$
E(z) = -\sum_{(i,j)\in E} J_{ij} z_i z_j + h_i z_i
$$

The gadget for suqare lattice QUBO problem is as follows

```
⋅ ⋅ ⋅ ⋅ ● ⋅ ⋅ ⋅ ⋅ 
○ ⋅ ● ⋅ ⋅ ⋅ ● ⋅ ○ 
⋅ ⋅ ⋅ ● ⋅ ● ⋅ ⋅ ⋅ 
⋅ ⋅ ⋅ ⋅ ○ ⋅ ⋅ ⋅ ⋅ 
```

where white circles have weight 1 and black circles have weight 2. The unit distance is `2.3`.
