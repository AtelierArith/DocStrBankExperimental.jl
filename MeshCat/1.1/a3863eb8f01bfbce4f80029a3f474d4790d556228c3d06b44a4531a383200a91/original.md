Set the transform of this visualizer's path. This can be done before or after adding an object at that path.

```julia
settransform!(
    vis::MeshCat.Visualizer,
    tform::CoordinateTransformations.Transformation
) -> MeshCat.Visualizer

```

The overall transform of an object is the composition of the transforms of all of its parents, so setting the transform of `vis[:group1]` affects the poses of the objects at `vis[:group1][:box1]` and `vis[:group1][:box2]`.
