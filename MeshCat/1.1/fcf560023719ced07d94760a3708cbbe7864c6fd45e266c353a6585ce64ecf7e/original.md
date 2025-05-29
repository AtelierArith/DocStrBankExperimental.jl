Set the object at this visualizer's path. This replaces whatever geometry was presently at that path.

```julia
setobject!(
    vis::MeshCat.Visualizer,
    obj::MeshCat.AbstractObject
) -> MeshCat.Visualizer

```

To draw multiple geometries, place them at different paths by using the slicing notation:

```
setobject!(vis[:group1][:box1], geometry1)
setobject!(vis[:group1][:box2], geometry2)
```
