```
t8_ghost_type_t
```

This type controls, which neighbors count as ghost elements. Currently, we support face-neighbors. Vertex and edge neighbors will eventually be added.

| Enumerator        | Note                                                             |
|:----------------- |:---------------------------------------------------------------- |
| T8_GHOST_NONE     | Do not create ghost layer.                                       |
| T8_GHOST_FACES    | Consider all face (codimension 1) neighbors.                     |
| T8_GHOST_EDGES    | Consider all edge (codimension 2) and face neighbors.            |
| T8_GHOST_VERTICES | Consider all vertex (codimension 3) and edge and face neighbors. |
