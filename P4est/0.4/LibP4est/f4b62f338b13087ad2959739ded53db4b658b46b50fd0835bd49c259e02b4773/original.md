```
p4est_mesh_t
```

This structure contains complete mesh information on a 2:1 balanced forest. It stores the locally relevant neighborhood, that is, all locally owned quadrants and one layer of adjacent ghost quadrants and their owners.

For each local quadrant, its tree number is stored in quad_to_tree. The quad_to_tree array is NULL by default and can be enabled using p4est*mesh*new*ext. For each ghost quadrant, its owner rank is stored in ghost\*to_proc. For each level, an array of local quadrant numbers is stored in quad_level. The quad_level array is NULL by default and can be enabled using p4est*mesh*new_ext.

The quad_to_quad list stores one value for each local quadrant's face. This value is in 0..local_num_quadrants-1 for local quadrants, or in local_num_quadrants + (0..ghost_num_quadrants-1) for ghost quadrants.

The quad_to_face list has equally many entries that are either: 1. A value of v = 0..7 indicates one same-size neighbor. This value is decoded as v = r * 4 + nf, where nf = 0..3 is the neighbor's connecting face number and r = 0..1 is the relative orientation of the neighbor's face; see [`p4est_connectivity`](@ref).h. 2. A value of v = 8..23 indicates a double-size neighbor. This value is decoded as v = 8 + h * 8 + r * 4 + nf, where r and nf are as above and h = 0..1 is the number of the subface. h designates the subface of the large neighbor that the quadrant touches (this is the same as the large neighbor's face corner). 3. A value of v = -8..-1 indicates two half-size neighbors. In this case the corresponding quad_to_quad index points into the quad_to_half array that stores two quadrant numbers per index, and the orientation of the smaller faces follows from 8 + v. The entries of quad_to_half encode between local and ghost quadrant in the same way as the quad_to_quad values described above. The small neighbors in quad_to_half are stored in the sequence of the face corners of this, i.e., the large quadrant.

A quadrant on the boundary of the forest sees itself and its face number.

The quad_to_corner list stores corner neighbors that are not face neighbors. On the inside of a tree, there is precisely one such neighbor per corner. In this case, its index is encoded as described above for quad_to_quad. The neighbor's matching corner number is always diagonally opposite, that is, corner number ^ 3.

On the inside of an inter-tree face, we have precisely one corner neighbor. If a corner is an inter-tree corner, then the number of corner neighbors may be any non-negative number. In both cases, the quad_to_corner value is in local_num_quadrants + local_num_ghosts + [0 .. local_num_corners - 1]. After subtracting the number of local and ghost quadrants, it indexes into corner_offset, which encodes a group of corner neighbors. Each group contains the quadrant numbers encoded as usual for quad_to_quad in corner_quad, and the corner number from the neighbor as corner_corner.

Corners with no diagonal neighbor at all are assigned the value -3. This only happens on the domain boundary, which is necessarily a tree boundary. Corner-neighbors for hanging nodes are assigned the value -1.

TODO: In case of an inter-tree corner neighbor relation in a brick-like situation (exactly one neighbor, diagonally opposite corner number), use the same encoding as for corners within a tree.

| Field         | Note                                                                                                                                                                                                  |
|:------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| quad_to_tree  | tree index for each local quad. Is NULL by default, but may be enabled by p4est*mesh*new_ext.                                                                                                         |
| ghost_to_proc | processor for each ghost quad                                                                                                                                                                         |
| quad_to_quad  | one index for each of the 4 faces                                                                                                                                                                     |
| quad_to_face  | encodes orientation/2:1 status                                                                                                                                                                        |
| quad_to_half  | stores half-size neighbors                                                                                                                                                                            |
| quad_level    | Stores lists of per-level quads. The array has entries indexed by 0..`P4EST_QMAXLEVEL` inclusive that are arrays of local quadrant ids. Is NULL by default, but may be enabled by p4est*mesh*new_ext. |
