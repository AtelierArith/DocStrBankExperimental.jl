```
p8est_iter_edge_info
```

The information about all sides of an edge in the forest. If tree_boundary is false, the edge is on the interior of a tree. When tree_boundary is false, sides[0] contains the lowest z-order quadrant that touches the edge. When tree_boundary is true, its value is P8EST_CONNECT_FACE/EDGE depending on the location of the edge relative to the tree.

| Field         | Note                                                  |
|:------------- |:----------------------------------------------------- |
| tree_boundary | boolean: interior face (0), tree boundary face (true) |
| sides         | array of `p8est_iter_edge_side_t` type                |
