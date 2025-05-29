```
p8est_get_plex_data_ext(p8est_, ghost, lnodes, ctype, overlap, first_local_quad, out_points_per_dim, out_cone_sizes, out_cones, out_cone_orientations, out_vertex_coords, out_children, out_parents, out_childids, out_leaves, out_remotes, custom_numbering)
```

Create the data necessary to create a PETsc DMPLEX representation of a forest, as well as the accompanying lnodes and ghost layer. The forest must be at least face balanced (see [`p4est_balance`](@ref)()). See test/test_plex2.c for example usage.

All arrays should be initialized to hold sizeof ([`p4est_locidx_t`](@ref)), except for *out_remotes*, which should be initialized to hold (2 * sizeof ([`p4est_locidx_t`](@ref))).

### Parameters

  * `p8est`:[in] the forest
  * `ghost`:[out] the ghost layer
  * `lnodes`:[out] the lnodes
  * `ctype`:[in] the type of adjacency for the overlap
  * `overlap`:[in] the number of layers of overlap (zero is acceptable)
  * `first_local_quad`:[out] the local quadrants are assigned contiguous plex indices, starting with this index
  * `out_points_per_dim`:[in,out] filled with argument for DMPlexCreateFromDAG()
  * `out_cone_sizes`:[in,out] filled with argument for DMPlexCreateFromDAG()
  * `out_cones`:[in,out] filled with argument for DMPlexCreateFromDAG()
  * `out_cone_orientations`:[in,out] filled with argument for DMPlexCreateFromDAG()
  * `out_vertex_coords`:[in,out] filled with argument for DMPlexCreateFromDAG()
  * `out_children`:[in,out] filled with argument for DMPlexSetTree()
  * `out_parents`:[in,out] filled with argument for DMPlexSetTree()
  * `out_childids`:[in,out] filled with argument for DMPlexSetTree()
  * `out_leaves`:[in,out] filled with argument for PetscSFSetGraph()
  * `out_remotes`:[in,out] filled with argument for PetscSFSetGraph()
  * `custom_numbering`:[in] Whether or use the default numbering (0) of DMPlex child ids or the custom (1).

### Prototype

```c
void p8est_get_plex_data_ext (p8est_t * p8est, p8est_ghost_t ** ghost, p8est_lnodes_t ** lnodes, p8est_connect_type_t ctype, int overlap, p4est_locidx_t * first_local_quad, sc_array_t * out_points_per_dim, sc_array_t * out_cone_sizes, sc_array_t * out_cones, sc_array_t * out_cone_orientations, sc_array_t * out_vertex_coords, sc_array_t * out_children, sc_array_t * out_parents, sc_array_t * out_childids, sc_array_t * out_leaves, sc_array_t * out_remotes, int custom_numbering);
```
