```
register_edgetype!(types::ModelTypes, ::Type{T}, [hints...; kwargs...])
```

Register an additional edge type to `types`. 

An edge type T is a structure that defines the state (field) of [`Edge{T}`](@ref).  These structs must be "bit types", that is, the type is immutable and contains only primitive types and other bit types. Often these types T are stateless, in which case they are used as a tag to distinguish between the existing types of edges of the model.

The internal data structures used to store the graph in memory can be modified by  the hints parameters:

  * `:IgnoreFrom`: The ID of the source agent is not stored. This implies that the state of the agents on the source of the edge is not accessible via e.g. the [`neighborstates`](@ref) function.
  * `:Stateless`: Store only the ID of the source agent.
  * `:SingleType`: All target agents have the same type, needs also keyword `target` (see below).
  * `:SingleEdge`: Each agent can be the target for max. one edge.
  * `:IgnoreSourceState`: The ID of the source agent is not used to access the state of the agent with this ID.
  * `:NumEdgesOnly`: Combines `:IgnoreFrom` and `:Stateless`
  * `:HasEdgeOnly`: Combines `:IgnoreFrom`, `:Stateless` and `:SingleEdge`

If `:SingleType` is set, the keyword argument `target` must be added. The value of this argument must be the type of the target node. If the `target` keyword exists, but the `:SingleType` hint is not explicitly specified, it will be set implicitly

If it is known how many agents of this type exist, this can also be specified via the optional `size` keyword. This can improve performance, but can also increase the memory usage.

A pipeable version of `register_edgetype!` is also available, enabling the construction of a Model via a sequence of `register_*` calls. This pipeline starts with `ModelTypes()` as the source and terminates in the [`create_model`](@ref) function as the destination.

See also [Edge Hints](./performance.md#Edge-Hints), [`add_edge!`](@ref) and  [`add_edges!`](@ref) 
