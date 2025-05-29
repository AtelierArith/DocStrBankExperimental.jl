```
expand!(ghost, forest, nodes)
```

Expand the ghost layer to include all elements with nodes shared with neighboring ranks.

Consider the following forest-of-quadtrees

```
+-------+---+---+
|       | 5 | 6 |
|   2   +---+---+
|       | 3 | 4 |
+-------+---+---+
|       |       |
|   0   |   1   |
|       |       |
+-------+-------+
```

that is partitioned so rank 0 owns quadrants {0,1} and rank 1 owns quadrants {2, 3, 4, 5, 6}.  A fully connected ghost layer on rank 0 would include quadrants {2, 3, 4}.  QuadrantWrapper 5 shares a global node with rank 0 but is not in the fully connected ghost layer.  This function expands the ghost layer to include quadrants like this.

See [`sharers`](@ref) to get a list of the global nodes shared with neighboring ranks.
