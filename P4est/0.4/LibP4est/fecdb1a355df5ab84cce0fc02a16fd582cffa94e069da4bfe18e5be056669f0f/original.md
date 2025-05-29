```
p4est_iter_face_info
```

The information that is available to the user-defined [`p4est_iter_face_t`](@ref) callback.

The orientation is 0 if the face is within one tree; otherwise, it is the same as the orientation value between the two trees given in the connectivity. If the face is on the outside boundary of the forest, then there is only one side. If tree_boundary is false, the face is on the interior of a tree. When tree_boundary is false, sides[0] contains the lowest z-order quadrant that touches the face. When tree_boundary is true, its value is P4EST_CONNECT_FACE.

| Field         | Note                                                                                               |
|:------------- |:-------------------------------------------------------------------------------------------------- |
| orientation   | the orientation of the sides to each other, as in the definition of [`p4est_connectivity_t`](@ref) |
| tree_boundary | boolean: interior face (0), tree boundary face (true)                                              |
