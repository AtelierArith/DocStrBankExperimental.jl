```
abaqus_read_model(filename::String)
```

Read ABAQUS model from file. Include also boundary conditions, load steps and so on. If only mesh is needed, it's better to use `abaqus_read_mesh` insted.
