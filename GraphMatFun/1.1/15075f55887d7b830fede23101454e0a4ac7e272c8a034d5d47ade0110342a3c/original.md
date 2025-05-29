```
rename_node!(graph,src,dest,cref=Vector())
```

This changes the name of the node `src` to `dest` and updates all references to the node, including coefficient references in `cref` and `graph.outputs`.
