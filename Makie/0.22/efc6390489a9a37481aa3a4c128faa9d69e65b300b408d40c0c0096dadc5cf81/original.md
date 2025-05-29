```
pick(fig/ax/scene, x, y[, range])
pick(fig/ax/scene, xy::VecLike[, range])
```

Returns the plot and element index under the given pixel position `xy = Vec(x, y)`. If `range` is given, the nearest plot up to a distance of `range` is returned instead.

The `plot` returned by this function is always a primitive plot, i.e. one that is not composed of other plot types.

The index returned relates to the main input of the respective primitive plot.

  * For `scatter` and `meshscatter` it is an index into the positions given to the plot.
  * For `text` it is an index into the merged character array.
  * For `lines` and `linesegments` it is the end position of the selected line segment.
  * For `image`, `heatmap` and `surface` it is the linear index into the matrix argument of the plot (i.e. the given image, value or z-value matrix) that is closest to the selected position.
  * For `voxels` it is the linear index into the given 3D Array.
  * For `mesh` it is the largest vertex index of the picked triangle face.
  * For `volume` it is always 0.

See also: `pick_sorted`
