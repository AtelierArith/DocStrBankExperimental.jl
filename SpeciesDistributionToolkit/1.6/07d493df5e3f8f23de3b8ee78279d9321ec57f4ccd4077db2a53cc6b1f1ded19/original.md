```
SimpleSDMLayers.mosaic(f, layer, polygons)
```

Overload of the mosaic function where the layer is split according to the polygons given as the last argument, and then the function `f` is applied to all the zones defined this way. The `f` function can take both positional and keyword arguments.
