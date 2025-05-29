Function for reading gmsh's mesh format files http://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format

```
Input:
    - mshFilename: the name of the .msh file to be read

Output:
    - nodesMat: matrix with 4 columns: [x y z physicalTag]
    - conecMat: matrix with 5 columns: [ n1 n2 n3 n4 physicalTag ] for elements with less than four nodes 0 is used as node index.
    - physicalNames: cell with strings of physical names.

Assumptions:
    - physical names are saved as strings
    - maximum of one physical tag per entity
    - maximum number of nodes per element: 4 (linear tetrahedron)
```
