```
byzone(f, layer::SDMLayer, polygons, polygonsnames = 1:length(polygons))
```

Applies the function `f` to all cells that belong to the same polygon, and returns the output as a dictionary. The function given as an argument can take both positional and keyword arguments.
