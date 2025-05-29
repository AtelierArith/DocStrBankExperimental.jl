```
render!(sm::SolidModel, cs::AbstractCoordinateSystem{T}; map_meta=layer, postrender_ops=[], zmap=(_) -> zero(T), kwargs...) where {T}
```

Render `cs` to `sm`.

# Keywords

  * `map_meta`: Function (m::SemanticMeta) -> name of `PhysicalGroup` (as `String` or `Symbol`; may also return `nothing` to skip rendering `m`)
  * `postrender_ops`: Vector of Tuples `(destination, op, args, op_kwargs...)` specifying "postrendering" of `PhysicalGroup`s executed after entities have been rendered to to `sm`. Each operation `op` creates a new `PhysicalGroup` defined as `sm[destination] = op(sm, args...; op_kwargs...)`. That is, `args` are the arguments to `op` (following the first argument, which is always the model `sm` being rendered to). For most operations, these arguments include the names and dimensions of groups being operated on, and `op_kwargs` are the keyword arguments passed to `op`. For example, `("base", difference_geom!, ("writeable_area", "base_negative"), :remove_object => true, :remove_tool => true)` defines a postrendering step that subtracts the `PhysicalGroup` named `"base_negative"` from `"writeable_area"` (by default using dimension 2 for each group) to define a new group called `"base"`. The keyword pairs `:remove_object=>true` and `:remove_tool=>true` mean that the "object" (first argument) group `"writeable_area"` and the "tool" (second argument) group `"base_negative"` are both removed when `"base"` is created.
  * `zmap`: Function (m::SemanticMeta) -> `z` coordinate of corresponding elements. Default: Map all metadata to zero.
  * `meshing_parameters`: `MeshingParameters` allows customization of the top level meshing parameters when calling Gmsh.

Available postrendering operations are [`translate!`](@ref), [`extrude_z!`](@ref), [`revolve!`](@ref), [`union_geom!`](@ref), [`intersect_geom!`](@ref), [`difference_geom!`](@ref), [`fragment_geom!`](@ref), and [`box_selection`](@ref). (The geometric Boolean operations are only available for models using the OpenCASCADE kernel.)

Additional keyword arguments are passed to [`SolidModels.to_primitives`](@ref) (which falls back to [`to_polygons`](@ref)) and may be used for certain entity types to control how entities of `cs` are converted to primitives and added to `sm`.
