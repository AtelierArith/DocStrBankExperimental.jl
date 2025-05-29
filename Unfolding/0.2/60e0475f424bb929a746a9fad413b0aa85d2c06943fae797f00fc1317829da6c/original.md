```
to_vtk(outname, coordinates, props)
```

Export the `coordinates` as VTK points named `outname`.vtu. Optionally, extra properties are passed via `props` as `NamedTuple` or `Dict`, where the first item is the property name and the second is an array with the property values.
