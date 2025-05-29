```
find_memory_for_type(root, typ::Type)::Union(Nothing, AbstractMemoryNode}
```

If there's a memory node in the Rete represented by `root` that stores objects of the specified type then return it.  Otherwise return nothing.
