```
attach!(g::SchematicGraph,
    pathnode::S,
    nodehook2::Pair{T, Symbol},
    position;
    i=lastindex(component(pathnode)),
    location=0) where {S <: ComponentNode, T <: ComponentNode}
Usage: attach!(g, pathnode, node2=>:hook2, position; i=segment_idx, location=0)
```

Adds an edge to `g` between `pathnode` and `node2`, attaching `:hook2` to a specified point along `pathnode`.

A new `HandedPointHook` is generated a distance `position` along the segment specified by `i`. If `location` is +1 or -1, the generated hook is offset to the right or left of the segment by the extent defined by the path's style, with the hook's inward direction pointing back to the segment.
