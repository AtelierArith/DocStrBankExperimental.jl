This function wrap from [NetworkX](https://github.com/networkx/networkx)

Position nodes on a circle.

**Parameters**

*g* a graph

**Returns**

*locs*x, locs*y* Locations of the nodes. Can be any units you want, but will be normalized and centered anyway

**Examples**

```
julia> g = smallgraph(:house)
julia> locs_x, locs_y = circular_layout(g)
```
