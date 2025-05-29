Add images to the current plot.

```
  plotimage([plotobj,] texturefile, vertices; label=nothing, _overwrite_label=false)
```

The `texturefile` string should include the path (relative or absolute) to the image to be loaded (if not in the current folder). The `vertices` array should be a set of vertex positions specifying the corners of the image to plot. The order is anticlockwise starting from bottom left (i.e. (0,1), (1,1), (1,0), (0,0) in texture coordinates), and the vertices should be specified as a 3x4 array. The `plotobj` argument is optional and determines which plot window to send the data to.  If it's not used the data will be sent to the plot window returned by `current()`.
