```
BOUNDARY(self::AbaqusExporter, NSET::AbstractString, dof::Integer,
  value::F) where {F}
```

Write out the `*BOUNDARY` option to fix displacements at nonzero value for a node set.

  * `NSET`= node set,
  * `dof`=Degree of freedom, 1, 2, 3
  * `typ` = DISPLACEMENT
