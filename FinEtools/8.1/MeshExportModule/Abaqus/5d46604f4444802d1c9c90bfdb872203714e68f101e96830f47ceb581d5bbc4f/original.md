```
BOUNDARY(self::AbaqusExporter, mesh, nodes, is_fixed::AbstractArray{B,2}, fixed_value::AbstractArray{F,2}) where {B, F}
```

Write out the `*BOUNDARY` option. 

The boundary condition is applied to the nodes specified in  the array `nodes`, in the mesh (or node set) `meshornset`.

`meshornset` = mesh or node set (default is empty) `nodes` = array of node numbers, the node numbers are attached to the mesh label, `is_fixed`= array of Boolean flags (true means fixed, or prescribed),  one row per node, `fixed_value`=array of displacements to which the corresponding displacement components is fixed

# Example

```
BOUNDARY(AE, "ASSEM1.INSTNC1", 1:4, fill(true, 4, 1), reshape([uy(fens.xyz[i, :]...) for i in 1:4], 4, 1))
```
