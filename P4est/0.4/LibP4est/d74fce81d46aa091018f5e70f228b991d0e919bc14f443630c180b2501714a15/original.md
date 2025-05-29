```
p8est_iter_face_side
```

Information about one side of a face in the forest. If a *quad* is local (*is_ghost* is false), then its *quadid* indexes the tree's quadrant array; otherwise, it indexes the ghosts array. If the face is hanging, then the quadrants are listed in z-order. If a quadrant should be present, but it is not included in the ghost layer, then quad = NULL, is_ghost is true, and quadid = -1.

| Field      | Note                                                 |
|:---------- |:---------------------------------------------------- |
| treeid     | the tree on this side                                |
| face       | which quadrant side the face touches                 |
| is_hanging | boolean: one full quad (0) or four smaller quads (1) |
