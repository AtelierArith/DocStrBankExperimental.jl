```
BOUNDARY(self::AbaqusExporter, meshornset, is_fixed::AbstractArray{B,2}, fixed_value::AbstractArray{F,2}) where {B, F}
```

Write out the `*BOUNDARY` option.

  * `meshornset` = name of a mesh or a node set,
  * `is_fixed`= array of Boolean flags (true means fixed, or prescribed),  one row per node, as many columns as there are degrees of freedom per node,
  * `fixed_value`=array of displacements to which the corresponding displacement components is fixed, as many columns as there are degrees of freedom per node
