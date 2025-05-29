```
t8_cmesh_get_face_neighbor(cmesh, ltreeid, face, dual_face, orientation)
```

Given a local tree id and a face number, get information about the face neighbor tree.

!!! note
    If *ltreeid* is a ghost and it has a neighbor which is neither a local tree or ghost, then the return value will be negative. Thus, a negative return value does not necessarily mean that this is a domain boundary. To find out whether a tree is a domain boundary or not


# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `ltreeid`:[in] The local id of a tree or a ghost.
  * `face`:[in] A face number of the tree/ghost.
  * `dual_face`:[out] If not NULL, the face number of the neighbor tree at this connection.
  * `orientation`:[out] If not NULL, the face orientation of the connection.

# Returns

If non-negative: The local id of the neighbor tree or ghost. If negative: There is no neighbor across this face. *dual_face* and *orientation* remain unchanged.

# See also

[`t8_cmesh_tree_face_is_boundary`](@ref).

### Prototype

```c
t8_locidx_t t8_cmesh_get_face_neighbor (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid, const int face, int *dual_face, int *orientation);
```
