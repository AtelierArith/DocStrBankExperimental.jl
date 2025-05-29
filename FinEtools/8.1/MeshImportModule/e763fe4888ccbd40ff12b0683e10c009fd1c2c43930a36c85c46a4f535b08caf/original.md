```
import_ABAQUS(filename)
```

Import Abaqus mesh (.inp file).

Limitations:

1. Only the `*NODE` and `*ELEMENT`  sections are read
2. Only 4-node and 10-node tetrahedra, 8-node or 20-node  hexahedra, 4-node quadrilaterals, 3-node triangles are handled.

# Output

Data dictionary, with keys 

  * "`fens`" = finite element nodes.
  * "`fesets`" = array of finite element sets.
  * "`nsets`" = dictionary of "node sets", the keys are the names of the sets.
