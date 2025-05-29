```
import_NASTRAN(filename)
```

Import tetrahedral (4- and 10-node) NASTRAN mesh (.nas file).

Limitations:

1. only the GRID, CTETRA, and PSOLID sections are read.
2. Only 4-node and 10-node tetrahedra  are handled.
3. The file should be free-form (data separated by commas).

Some fixed-format files can also be processed (large-field, but not small-field).

# Output

Data dictionary, with keys 

  * "`fens`": set of finite element nodes,
  * "`fesets`": array of finite element sets,
  * "`property_ids`": array of property ids (integers) associated with the finite element sets.
