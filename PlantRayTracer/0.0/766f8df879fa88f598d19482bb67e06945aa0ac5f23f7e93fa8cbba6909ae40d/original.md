```
accelerate(mesh::Mesh; settings = RTSettings(), acceleration = Naive, rule = nothing)
```

Create an `AccMesh` object from a mesh, settings and acceleration function (choose from `Naive` or  `BVH`). The argument `rule` is only required for the accelerator `BVH` and it must be an object of type `SAH` or `AvgSplit` (it is ignored for the `Naive` accelerator). The `AccMesh` object contains the acceleration structure and the grid cloner structure built on top of the original 3D meshes in `mesh`. See VPL documentation for details.

## Examples

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> acc = accelerate(mesh);
```
