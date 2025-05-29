```
struct MeshSized{T, S} <: GeometryEntityStyle where {T, S <: Real}
    h::T
    α::S
end
```

Style that annotates a GeometryEntity with a mesh size to use in SolidModel rendering. The generated mesh will include a size field defined as:

```
mesh size = `h` * max(`s_g`, (d/`h`)^`α`)
```

where d is the distance away from the styled entity, and `s_g` is the global mesh scale parameter specified in `MeshingParameters`. A smaller value of `h` will give a finer mesh attached to the styled entity, and a larger value of `α` will give a more rapid increase in size away from the styled entity.

For `α < 0`, the size field will use `α_default` from the `MeshingParameters` used in rendering.

See also [`meshsized_entity`](@ref) and [`SolidModels.MeshingParameters`](@ref).
