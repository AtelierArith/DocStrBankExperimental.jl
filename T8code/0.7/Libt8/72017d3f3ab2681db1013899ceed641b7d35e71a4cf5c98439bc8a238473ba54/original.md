```
t8_forest_ltreeid_to_cmesh_ltreeid(forest, ltreeid)
```

Given the local id of a tree in a forest, compute the tree's local id in the associated cmesh.

!!! note
    For forest local trees, this is the inverse function of t8*forest*cmesh*ltreeid*to_ltreeid.


# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] The local id of a tree or ghost in the forest.

# Returns

The local id of the tree in the cmesh associated with the forest. *forest* must be committed before calling this function.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_locidx_t t8_forest_ltreeid_to_cmesh_ltreeid (t8_forest_t forest, t8_locidx_t ltreeid);
```
