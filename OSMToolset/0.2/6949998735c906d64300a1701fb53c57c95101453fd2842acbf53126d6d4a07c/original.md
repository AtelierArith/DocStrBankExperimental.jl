```
findnode(sindex::NodeSpatIndex, point::Union{LLA, ENU})
```

Find the node in the `sindex` spatial index closest to the given `point` coordinates.

Returns a named tuple of the `distance` and the `nodeid`. When no node is found within the `node_range` of `sindex` the `nodeid` is set to `0` and the `distance` to `Inf`.
