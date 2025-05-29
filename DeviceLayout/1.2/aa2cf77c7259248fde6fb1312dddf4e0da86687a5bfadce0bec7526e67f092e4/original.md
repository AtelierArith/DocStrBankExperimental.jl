```
meshsized_entity(ent::GeometryEntity, h::T, α::S=-1.0) where {T, S <: Real}
```

Create a [`MeshSized`](@ref) entity, specifying a mesh size use in SolidModel rendering. The generated mesh will include a size field defined as:

```
mesh size = `h` * max(`s_g`, (d/`h`)^`α`)
```

where d is the distance away from the styled entity, and `s_g` is the global mesh scale parameter specified in `MeshingParameters`. A smaller value of `h` will give a finer mesh attached to the styled entity, and a larger value of `α` will give a more rapid increase in size away from the styled entity.

For `α < 0`, the size field will use `α_default` from the [`SolidModels.MeshingParameters`](@ref) used in rendering.
