The information that is availalbe to the user-defined [`p8est_iter_corner_t`](@ref) callback.

If tree_boundary is false, the corner is on the interior of a tree. When tree_boundary is false, sides[0] contains the lowest z-order quadrant that touches the corner. When tree_boundary is true, its value is P8EST_CONNECT_FACE/EDGE/CORNER depending on the location of the corner relative to the tree.
