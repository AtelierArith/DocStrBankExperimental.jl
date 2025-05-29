```
export_gml(fpn::String, G::AbstractGraph{::Integer}, kwargs...)
```

Save the graph `G` as a .gml file.

`G` can be either a `FlipGraph` or `FlipGraphPlanar`.

# Arguments

  * vertex_attributes::Vector{Dict} : If provided, the `i`-th vertex gets the attributes from the `i`-th `Dict`.                                    Each `key`, `value` pair defines an attribute, where the `key` is the name of the attribute and `value` is its value.
  * edge_attributes::Vector{Dict}   : If provided, the `i`-th edge gets the attributes from the `i`-th `Dict`.                                    Each `key`, `value` pair defines an attribute, where the `key` is the name of the attribute and `value` is its value.
  * add_diameter = false :            If set to true, every vertex in the exported tree gets an attribute called diameter with the respective diameter of the `DeltaComplex` of that vertex.

# Examples

```julia-repl
julia> G = flipgraph_planar(10);
julia> export_gml("C:/Users/USERNAME/Desktop/filename.gml", G);
```

By adding the additional symbol `:diameter`, the nodes get a value *diameter* which corresponds to the diameter of the `DeltaComplex` or `TriangulatedPolygon` it models. Be aware however, that this diameter is computed on the run and will therefore significantly slow down this export method.

```julia-repl
julia> G = flipgraph_modular(1,3,labeled_points = true);
julia> export_gml("C:/Users/USERNAME/Desktop/filename.gml", G, add_diameter=true);
```
