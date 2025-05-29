```
getslicecell(meta, sliceoffset, dir, minCoord, maxCoord) -> idlist, indexlist
```

Find the cell IDs `idlist` which are needed to plot a 2d cut through of a 3d mesh, in a direction `dir` at `sliceoffset`, and the `indexlist`, which is a mapping from original order to the cut plane and can be used to select data onto the plane.
