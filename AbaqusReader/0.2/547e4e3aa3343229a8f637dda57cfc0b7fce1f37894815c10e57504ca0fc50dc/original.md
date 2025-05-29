```
abaqus_read_mesh(fn::String)
```

Read ABAQUS mesh from file `fn`. Returns a dict with elements, nodes, element sets, node sets and other topologically imporant things, but not the actual model with boundary conditions, load steps and so on.
