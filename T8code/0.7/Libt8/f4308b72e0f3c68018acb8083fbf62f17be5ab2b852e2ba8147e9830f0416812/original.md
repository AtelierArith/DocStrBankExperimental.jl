```
t8_forest_cmesh_ltreeid_to_ltreeid(forest, lctreeid)
```

Given the local id of a tree in the coarse mesh of a forest, compute the tree's local id in the forest.

!!! note
    For forest local trees, this is the inverse function of t8*forest*ltreeid*to*cmesh_ltreeid.


# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] The local id of a tree in the coarse mesh of *forest*.

# Returns

The local id of the tree in the forest. -1 if the tree is not forest local. *forest* must be committed before calling this function.

# See also

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing for more details about tree indexing.

### Prototype

```c
t8_locidx_t t8_forest_cmesh_ltreeid_to_ltreeid (t8_forest_t forest, t8_locidx_t lctreeid);
```
