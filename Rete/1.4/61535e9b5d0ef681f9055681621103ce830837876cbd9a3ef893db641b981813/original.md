```
ensure_memory_node(root::AbstractReteRootNode, typ::Type)::IsaTypeNode
```

Find a memory node for the specified type, or make one and add it to the network.

The default is to make an IsaMemoryNode.  Specialize this function for a `Type` to control what type of memory node should be used for that type.
