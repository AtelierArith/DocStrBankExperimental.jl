```
BOUNDARY(self::AbaqusExporter, NSET::AbstractString, dof::Integer,  fixed_value)
```

Write out the `*BOUNDARY` option.

  * `NSET` = name of a node set,
  * `is_fixed`= array of Boolean flags (true means fixed, or prescribed),  one row per node,
  * `fixed_value`=array of displacements to which the corresponding displacement components is fixed
