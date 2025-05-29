```
Network([g,] vertexf, edgef; kwarg...)
```

Construct a `Network` object from a graph `g` and edge and component models `vertexf` and `edgef`.

Arguments:

  * `g::AbstractGraph`: The graph on which the network is defined.  Optional, can be ommittet if all component models have a defined `graphelement`.  See `vidx` and `src`/`dst` keywors for [`VertexModel`](@ref) and [`EdgeModel`](@ref) constructors respectively.
  * `vertexm`:  A single [`VertexModel`](@ref) or a vector of [`VertexModel`](@ref) objects.  The order of the vertex models must mirror the order of the `vertices(g)` iterator.
  * `edgem`: A single [`EdgeModel`](@ref) or a vector of [`EdgeModel`](@ref) objects.  The order of the edge models must mirror the order of the `edges(g)` iterator.

Optional keyword arguments:

  * `execution=SequentialExecution{true}()`:  Execution model of the network. E.g. [`SequentialExecution`](@ref), [`KAExecution`](@ref), [`PolyesterExecution`](@ref) or [`ThreadedExecution`](@ref).
  * `aggregator=execution isa SequentialExecution ? SequentialAggregator(+) : PolyesterAggregator(+)`:  Aggregation function applied to the edge models. E.g. [`SequentialAggregator`](@ref), [`PolyesterAggregator`](@ref), [`ThreadedAggregator`](@ref), [`SparseAggregator`](@ref).
  * `check_graphelement=true`:  Check if the `graphelement` metadata is consistent with the graph.
  * `dealias=false`  Check if the components alias eachother and create copies if necessary.  This is necessary if the same component model is referenced in multiple places in the Network but you want to  dynamicially asign metadata, such as initialization information to specific instances.
  * `verbose=false`:  Show additional information during construction.
