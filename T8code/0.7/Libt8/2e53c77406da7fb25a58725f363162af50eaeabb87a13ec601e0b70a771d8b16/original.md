```
t8_stash_add_facejoin(stash, gid1, gid2, face1, face2, orientation)
```

Add a face connection to a stash.

# Arguments

  * `stash`:[in,out] The stash to be updated.
  * `id1`:[in] The global id of the first tree.
  * `id2`:[in] The global id of the second tree,
  * `face1`:[in] The face number of the face of the first tree.
  * `face2`:[in] The face number of the face of the second tree.
  * `orientation`:[in] The orientation of the faces to each other.

### Prototype

```c
void t8_stash_add_facejoin (t8_stash_t stash, t8_gloidx_t gid1, t8_gloidx_t gid2, int face1, int face2, int orientation);
```
