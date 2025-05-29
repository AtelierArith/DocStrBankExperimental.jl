```
transformation(sch::Schematic, node::ComponentNode)
```

Given a Schematic `sch` containing [`ComponentNode`](@ref) `node` in its `SchematicGraph`, this function returns a `CoordinateTransformations.Transformation` object that lets you translate from the coordinate system of the node to the global coordinate system of `sch`.

Effectively a wrapper around `DeviceLayout.transformation(::CoordinateSystem, ::CoordSysRef)`.
