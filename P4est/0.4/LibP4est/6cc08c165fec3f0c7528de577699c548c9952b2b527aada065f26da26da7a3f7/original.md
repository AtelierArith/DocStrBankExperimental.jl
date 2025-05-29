```
p4est_connectivity_join_faces(conn, tree_left, tree_right, face_left, face_right, orientation)
```

[`p4est_connectivity_join_faces`](@ref) This function takes an existing valid connectivity *conn* and modifies it by joining two tree faces that are currently boundary faces.

### Parameters

  * `conn`:[in,out] connectivity that will be altered.
  * `tree_left`:[in] tree that will be on the left side of the joined faces.
  * `tree_right`:[in] tree that will be on the right side of the joined faces.
  * `face_left`:[in] face of *tree_left* that will be joined.
  * `face_right`:[in] face of *tree_right* that will be joined.
  * `orientation`:[in] the orientation of *face_left* and *face_right* once joined (see the description of [`p4est_connectivity_t`](@ref) to understand orientation).

### Prototype

```c
void p4est_connectivity_join_faces (p4est_connectivity_t * conn, p4est_topidx_t tree_left, p4est_topidx_t tree_right, int face_left, int face_right, int orientation);
```
